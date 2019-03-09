This page details how to create the JetBot SD card image from scratch.

This is useful in case you want to distribute a modified version of the JetBot SD card image.

1. Flash SD card by following Jetson Nano getting started guide.  
    * Use the username / password ``jetbot`` / ``jetbot``
    * Make sure to ``log in automatically``
2. Insert SD card into Jetson Nano and power on
3. Enable i2c permissions
    
    ```bash
    sudo usermod -aG i2c $USER
    ```
4. Upgrade numpy
    ```bash
    sudo apt-get update
    sudo apt install python3-pip
    sudo pip3 install --upgrade numpy
    ```
4. Install the pre-built TensorFlow [pip wheel](https://drive.google.com/open?id=1kphud0UiBZCXzRIZp9RY5xpfbt94n0mM) we provide for this project.

    ```bash
    sudo pip3 install tensorflow-1.8.0-cp36-cp36m-linux_aarch64.whl
    ```
4. Install the pre-built PyTorch [pip wheel](https://drive.google.com/open?id=1Eq641Jqb2Q0KBKsVpAhU-vxB_Mqcfrjd) we provide for this project.

    ```bash
    sudo pip3 install torch-1.0.0a0+18eef1d-cp36-cp36m-linux_aarch64.whl
    ```
5. Install traitlets (master, to support the ``unlink()`` method)

    ```bash
    sudo python3 -m pip install git+https://github.com/ipython/traitlets@master
    ```
6. Install jupyter lab

    ```bash
    sudo apt install nodejs npm
    sudo pip3 install jupyter jupyterlab
    sudo jupyter labextension install @jupyter-widgets/jupyterlab-manager
    sudo jupyter labextension install @jupyterlab/statusbar
    jupyter lab --generate-config
    jupyter notebook password
    ```
    You should then enter the password ``jetbot`` (unless you want to use a custom password).
7. Install this repo

    ```bash
    cd
    sudo apt install python3-smbus
    git clone https://github.com/NVIDIA-AI-IOT-private/jetbot
    cd jetbot
    sudo apt-get install cmake
    sudo python3 setup.py install
    ```

8. Install jetbot services

    ```bash
    cd jetbot/utils
    python3 create_stats_service.py
    sudo mv jetbot_stats.service /etc/systemd/system/jetbot_stats.service
    sudo systemctl enable jetbot_stats
    sudo systemctl start jetbot_stats
    python3 create_jupyter_service
    sudo mv jetbot_jupyter.service /etc/systemd/system/jetbot_jupyter.service
    sudo systemctl enable jetbot_jupyter
    sudo systemctl start jetbot_jupyter
    ```

8. Make swapfile
    ```
    sudo fallocate -l 4G /var/swapfile
    sudo chmod 600 /var/swapfile
    sudo mkswap /var/swapfile
    sudo swapon /var/swapfile
    ```
 
9. Copy JetBot notebooks to home directory

    ```
    cp -r ~/jetbot/notebooks/robot ~/Notebooks
    ```
10. Download [ssd_mobilenet_v2_coco.engine](https://drive.google.com/open?id=1jNrw5aZweXCIh5if6OeFzfKEH1HsC4M5) to ``~/Notebooks/object_following/ssd_mobilenet_v2_coco.engine``

11. Download [best_model.pth](https://drive.google.com/open?id=1UsRax8bR3R-e-0-80KfH2zAt-IyRPtnW) to ``~/Notebooks/collision_avoidance/best_model.pth``

[![Analytics](https://ga-beacon.appspot.com/UA-135919510-1/jetbot/wiki/Create-SD-Card-Image-From-Scratch/?pixel)](https://github.com/igrigorik/ga-beacon)