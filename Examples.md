Assuming you've followed the software setup and your robot is connected to the WiFi, you're
ready to run the JetBot examples.  All the examples run using *Jupyter notebooks*, which are
special documents that combine text editing, programming, and graphical display.

The examples notebooks can be accessed by navigating to ``http://<jetbot_ip_address>:8888``,
signing in with the password ``jetbot``, and navigating to the directory ``~/Notebooks``.

[[_TOC_]]

### Basic Motion

In the first example we'll learn the basics of making JetBot move around.  You should get a good feeling
for how the motor commands effect the movement of the robot.

1. Connect to your robot by navigating to ``http://<jetbot_ip_address>:8888``
2. Shutdown all other running notebooks by selecting ``Kernel`` -> ``Shutdown All Kernels...``
3. Open and follow the ``basic_motion.ipynb`` notebook

> All paths mentioned for this example are relative to ``~/Notebooks/basic_motion``

### Teleoperation

> This example requires a gamepad controller connected to your workstation.

In this example we'll drive the robot remotely from our desktop computer, view live streaming video, and save snapshots!

1. Connect to your robot by navigating to ``http://<jetbot_ip_address>:8888``
2. Shutdown all other running notebooks by selecting ``Kernel`` -> ``Shutdown All Kernels...``
3. Open and follow the ``teleoperation.ipynb`` notebook

> All paths mentioned for this example are relative to ``~/Notebooks/teleoperation``

### Collision avoidance

In this example we'll collect an *image classification* dataset that will be used to help keep
your JetBot safe!  We'll teach the JetBot to detect two scenarios ``free`` and ``blocked``.  We'll use this AI classifier to prevent JetBot from entering dangerous territory.

1. Connect to your robot by navigating to ``http://<jetbot_ip_address>:8888``
2. Shutdown all other running notebooks by selecting ``Kernel`` -> ``Shutdown All Kernels...``
3. Open and follow the ``data_collection.ipynb`` notebook
    > We provide a pre-trained model in this example's directory on the robot.  If you just want to run the live demo you may skip to step 8.
4. Connect to your training machine by navigating to ``http://<training_machine_ip_address>:8888``
5. Open and follow the ``train_model.ipynb`` notebook
6. Connect back to your robot by navigating to ``http://<jetbot_ip_address>:8888``
7. Shutdown all other running notebooks by selecting ``Kernel`` -> ``Shutdown All Kernels...``
8. Open and follow the ``live_demo.ipynb`` notebook

<!--
### Example 4 - AI Lego city road following

In this demo you'll teach JetBot how to autonomously follow a road!  You'll use the same technique we used for collision avoidance, but we'll use three classes this time ``left``, ``forward``, ``right``.  Our training method is slightly modified to make the transition between classes a bit smoother too, which will help our robot drive smoothly.

We want to teach the robot to follow the road through all turns, and go forward through all intersections, so when labeling the data follow this guideline

1.  Should the robot turn left now to stay on track? Hit left.
2.  Should the robot turn right now to stay on track?  Hit right.
3.  Should the robot go forward now to stay on track?  Hit forward.


By now, we think you're pretty familiar with Jupyter notebooks, and operating the JetBot and your GPU training machine.  We'll leave you to explore these notebooks, they're found under ``Notebooks/lego_city/road_following``
-->

[![Analytics](https://ga-beacon.appspot.com/UA-135919510-1/jetbot/wiki/Examples/?pixel)](https://github.com/igrigorik/ga-beacon)