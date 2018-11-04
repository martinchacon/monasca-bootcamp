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

* Clone the bootcamp
    ```bash
    git clone https://github.com/martinchacon/monasca-bootcamp.git
    ```
