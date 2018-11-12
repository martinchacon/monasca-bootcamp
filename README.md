# OpenStack Summit Berlin 2018

## Monitoring Hands-On Workshop

## Monasca Bootcamp

---

* Download your private SSH key (monasca-bootcamp-2018.pem) from
  [here](https://chaconpiza.com/monasca-berlin2018.pem).

* Change permissions

    ```bash
    chmod 600 monasca-bootcamp-2018.pem
    ```

* SSH to your instance and pull the Bootcamp

    ```bash
    ssh -i monasca-bootcamp.pem ubuntu@<your_instance_ip>
    cd monasca-bootcamp
    git pull
   ```

* Start the notebook

    ```bash
    /opt/jupyter/bin/jupyter notebook --no-browser --ip=<your_instance_ip>  --port=8889 --notebook-dir .
   ```

* Copy the URL and open it in your local browser.

* Open `MonascaBootcamp.ipynb` notebook.

### For Windows users

* You can use your favorite SSH client.

* We recommend Git BASH, BASH emulator with SSH client.

* Another good alternative is [cmder](http://cmder.net/).

#### For PuTTY users

* Set the private key for authentication in `Connection -> SSH -> Auth`.
  Choose [putty_key.ppk](https://chaconpiza.com/putty_key.ppk) as your private key.

* Remember to save the session settings.

## Running the notebook on your own

---

This is an iPython/Jupyter notebook that you can run on your own.
You will require:

* Ubuntu Linux 16.04

* and follow the [setup procedure](/setup/README.md)
