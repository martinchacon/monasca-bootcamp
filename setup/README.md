# OpenStack Summit Berlin 2018

## Monitoring Hands-On Workshop

## Environment Setup

---

* System

    Ubuntu 16.04, Processor: 2 CPU, Mem: 16 GB, Disk: 50 GB SSD.

* Update locale
    ```bash
    sudo update-locale LC_ALL=en_US.UTF-8
    sudo vi /etc/hosts # add monasca as localhost
    ```

* Install pip
    ```bash
    sudo apt-get update
    sudo apt-get install python-pip
    ```

* Install apache
    ```bash
    sudo apt-get install apache2 libapache2-mod-wsgi
    ```

* Install docker
    ```bash
    sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    sudo add-apt-repository    "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
       $(lsb_release -cs) \
       stable"
    sudo apt-get update
    sudo apt-get install docker-ce
    ```

* Add your user to the docker group
    ```bash
    sudo usermod -aG docker $USER
    ```

* Logout and login

* Install Docker Compose
    ```bash
    sudo curl -L https://github.com/docker/compose/releases/download/1.22.0/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
    sudo chmod +x /usr/local/bin/docker-compose
    ```

* Install Jupyter
    ```bash
    sudo apt-get install virtualenv
    sudo -s
    cd /opt
    virtualenv jupyter
    source jupyter/bin/activate
    pip install jupyter
    pip install -c http://git.openstack.org/cgit/openstack/requirements/plain/upper-constraints.txt?h=stable/rocky python-monascaclient
    deactivate
    exit
    ```

* Install stress-ng
    ```bash
    sudo apt-get install stress-ng
    ```

* Install django
    ```bash
    sudo pip install -c http://git.openstack.org/cgit/openstack/requirements/plain/upper-constraints.txt?h=stable/pike django
    ```

* install horizon
    ```bash
    git clone https://github.com/witekest/monasca-bootcamp.git
    git clone https://git.openstack.org/openstack/horizon -b stable/pike --depth=1
    pushd horizon
    sudo pip install -c http://git.openstack.org/cgit/openstack/requirements/plain/upper-constraints.txt?h=stable/pike .
    cp ~/monasca-bootcamp/setup/files/local_settings.py openstack_dashboard/local/local_settings.py
    popd
    ```

* install monasca-ui
    ```bash
    sudo pip install -c http://git.openstack.org/cgit/openstack/requirements/plain/upper-constraints.txt?h=stable/pike python-monascaclient
    git clone https://git.openstack.org/openstack/monasca-ui
    pushd monasca-ui
    sudo pip install -c http://git.openstack.org/cgit/openstack/requirements/plain/upper-constraints.txt?h=stable/pike .
    ln -f monitoring/enabled/_50_admin_add_monitoring_panel.py ~/horizon/openstack_dashboard/local/enabled/_50_admin_add_monitoring_panel.py
    ln -f monitoring/conf/monitoring_policy.json ~/horizon/openstack_dashboard/conf/monitoring_policy.json
    ln -sfF /home/ubuntu/monasca-ui/monitoring /home/ubuntu/horizon/monitoring
    cp ~/monasca-bootcamp/setup/files/monasca_local_settings.py monitoring/config/local_settings.py
    vi monitoring/config/local_settings.py
    # update GRAFANA_URL
    popd
    pushd /etc/apache2/sites-available/
    sudo cp ~/monasca-bootcamp/setup/files/horizon.conf .
    sudo rm ../sites-enabled/000-default.conf
    sudo ln -s ../sites-available/horizon.conf .
    popd
    ./horizon/manage.py collectstatic
    ./horizon/manage.py compress
    sudo a2ensite horizon
    sudo service apache2 restart
    ```

* Clone the bootcamp
    ```bash
    git clone https://github.com/martinchacon/monasca-bootcamp.git
    ```
