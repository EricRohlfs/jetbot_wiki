This page lists the examples provided with JetBot

> Make sure your robot is connected to WiFi as described in the [software setup](software-setup)

### 1. Basic Motion

In this example we'll control JetBot by programming from a web browser.

1. Connect to your robot by navigating to ``http://<jetbot_ip_address>:8888``
2. Open and follow the ``basic_motion.ipynb`` notebook

> All paths mentioned for this example are relative to ``~/Notebooks/basic_motion``

### 2. Teleoperation

> This example requires a gamepad controller connected to your workstation.

In this example we'll drive JetBot remotely, view live streaming video, and save snapshots!

1. Connect to your robot by navigating to ``http://<jetbot_ip_address>:8888``
2. Shutdown all other running notebooks by selecting ``Kernel`` -> ``Shutdown All Kernels...``
3. Open and follow the ``teleoperation.ipynb`` notebook

> All paths mentioned for this example are relative to ``~/Notebooks/teleoperation``

### 3. Collision avoidance

In this example we'll collect an *image classification* dataset that will be used to help keep
JetBot safe!  We'll teach JetBot to detect two scenarios ``free`` and ``blocked``.  We'll use this AI classifier to prevent JetBot from entering dangerous territory.

1. Connect to your robot by navigating to ``http://<jetbot_ip_address>:8888``
2. Shutdown all other running notebooks by selecting ``Kernel`` -> ``Shutdown All Kernels...``
3. Open and follow the ``data_collection.ipynb`` notebook
    > We provide a pre-trained model in this example's directory on the robot.  If you just want to run the live demo you may skip to step 8.
4. Connect to your training machine by navigating to ``http://<training_machine_ip_address>:8888``
5. Open and follow the ``train_model.ipynb`` notebook
6. Connect back to your robot by navigating to ``http://<jetbot_ip_address>:8888``
7. Shutdown all other running notebooks by selecting ``Kernel`` -> ``Shutdown All Kernels...``
8. Open and follow the ``live_demo.ipynb`` notebook

[![Analytics](https://ga-beacon.appspot.com/UA-135919510-1/jetbot/wiki/Examples/?pixel)](https://github.com/igrigorik/ga-beacon)