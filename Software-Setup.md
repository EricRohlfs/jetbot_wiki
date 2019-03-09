This page details the software setup required to run JetBot.

[[_TOC_]]

### Jetson Nano setup

Follow these steps to set up your Jetson Nano with all of the required JetBot software.

#### Booting Jetson Nano

1. Download the zip archieve of JetBot SD card image, [jetbot_image_v0p2p0.zip](https://drive.google.com/open?id=12WXOobOrX3ejWOMte6HEpUVXt0pNbi6f)
2. Insert a 64GB+ SD card into your desktop machine
3. Using [Etcher](https://www.balena.io/etcher/), select ``jetbot_image_v0p2p0.zip`` to flash the image to the SD card 
4. Remove the SD card from your desktop machine
5. Insert the SD card into your Jetson Nano (the micro SD card slot is located 
   under the module)
6. Connect the monitor, keyboard, and mouse to the Nano
7. Power on the Jetson Nano by connecting the micro USB charger to the micro USB port

Congratulations!  Your Jetson Nano should now boot and present the Ubuntu login screen!  Now you'll need to connect to the WiFi and optionally update the JetBot software.

#### Connecting to WiFi

1. Log into the ``jetbot`` user using the password ``jetbot``
2. Connect to a WiFi network using the Ubuntu desktop GUI

Your Jetson Nano should now automatically connect to the WiFi at boot and display it's IP address on the piOLED display.

#### Connecting to your robot from a web browser

Now that your Jetson Nano WiFi is configured, you're able to program your robot from a 
web browser on the same network!  This means that you shouldn't need to connect your robot
to a monitor past this step! 

1. Unplug your HDMI monitor, USB keyboard, and mouse from Jetson Nano.
2. Check the IP address of your robot on the *piOLED* display screen.  Enter this in place of ``<jetbot_ip_address>`` in the next command
3. Navigate to ``http://<jetbot_ip_address>:8888``

You should see the *Jupyter Lab* web programming environment load with a file browser, editor, and other tools. Jupyter Lab is a web based programming that enables the following 

* File browsing and editing
* Execution of Jupyter *Notebooks*, which mix text descriptions, executable code *cells* and graphics displays in a single hybrid document!
* File upload and downloading from your computer

Right above the file browser on the left size you should see a ``+`` icon.  This enables you to
launch notebooks, interactive Python programming shells, text editors, or a terminals.

#### Installing latest software (optional)

The software for controlling JetBot and accessing the camera is contained in the 
[jetbot](https://gitlab-master.nvidia.com/jwelsh/jetbot) Git repository.  

> In case you're unfamiliar, *Git* is a tool 
maintaining and co-developing software.  A Git repository is a collection of files
with an entire history of all changes, so if we ever make a mistake we can easily 
go back!  It also has lots of other tools that make it easy to work on the same
content with other people.

As a convenience, we pre-install this repository on the SD card image you downloaded 
to the path ``/home/jetbot/jetbot``.  
However, JetBot is a growing project that is rapidly evolving, with new examples and capabilities.  The SD card image you have may not have the latest and greatest.  To get the most up to date software, we can use
the Git tool from the linux *terminal*.  Use the *Jupyter Lab Launcher* to launch a terminal.  You'll be presented with a prompt to enter commands,
enter the following in sequence.

Pull the latest git repository
```bash
git clone https://gitlab-master.nvidia.com/jwelsh/jetbot
```

> For the internal beta, our software is hosted on NVIDIA gitlab-master.  You'll need to be connected to the corporate network in order to install the latest software.  You can either
skip this step for now, or connect your Nano to the corporate network via Ethernet.  

Re-install the ``jetbot`` Python package.

```bash
cd jetbot
python3 setup.py install --user
```

Then, you'll need to copy the example notebooks to the directory ``~/Notebooks`` (or a directory of your choosing).

```bash
mkdir ~/Notebooks
cp jetbot/notebooks/robot/* ~/Notebooks/
```

> If the Notebooks directory already exists (which it probably does), you can remove it with the following command
> ``rm -rf /home/jetbot/Notebooks`` and then try re-calling the above command.

You should now have the latest software installed and ready to use!  Before you can run the samples though, you'll need to assemble your robot as in the [hardware setup](hardware-setup).

#### Configuring power mode

To ensure that the Jetson Nano doesn't draw more current than the battery pack can supply,
place the Jetson Nano in ``5W`` mode by calling the following command

```bash
sudo nvpmodel -m1
```

### Training machine setup

> If you just want to test the robot, or use the pre-trained models, you can skip this step. 

Some of the examples require a separate machine for *training* the neural networks.  Training
is a very computationally intensive task that requires a GPU machine to iterative over lots
of data samples.

To run the training examples, you'll need a GPU enabled desktop or cloud instance with PyTorch installed. Once you have that, clone and install the JetBot repository

#### Docker container

1. Follow these instructions to install docker-ce https://docs.docker.com/install/linux/docker-ce/ubuntu/
2. Instructions at https://github.com/NVIDIA/nvidia-docker to install nvidia-docker

Then you'll need to reload the docker daemon before you can use nvidia-docker

```bash
sudo systemctl daemon-reload
sudo systemctl restart docker
```

Then, you can launch the docker container by calling

```bash
export NV_GPU=1
sudo docker run --runtime=nvidia -it -p 8888:8888 gitlab-master.nvidia.com:5005/jwelsh/jetbot/jetbot-host:v0.2.0
```

> You may need to change the value of NV_GPU to match the GPU on your machine you want to use.  You can check this
> with by calling ``nvidia-smi`` in a terminal

> Please note, the ``Notebooks`` directory in the docker container will be cleared if you shutdown the container!
> If you want to save any changes, we suggest mounting a volume to the container at ``/dli/jetbot/<your volume>``

#### Manual setup

If you don't want to use the docker container, you can manually configure the training machine by following these steps.
You'll need PyTorch already installed on your training machine.

```bash
git clone https://gitlab-master.nvidia.com/jwelsh/jetbot
cd jetbot
python3 setup.py install --user
```

Then, you can create a directory containing the example *host* notebooks by calling

```bash
python3 -m jetbot.util.create_notebooks_dir --output_dir=Notebooks
```

### Next

Follow the [examples](examples) to get your JetBot hardware configured.


[![Analytics](https://ga-beacon.appspot.com/UA-135919510-1/jetbot/wiki/Software-Setup/?pixel)](https://github.com/igrigorik/ga-beacon)