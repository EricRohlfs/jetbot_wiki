This page has tips related to battery charging and usage for [this battery](https://amzn.to/2WRcIUe).

## Charging

The USB battery pack selected is very nice and affordable, but has some caveats we noticed...

1. USB output channels will momentarily power down when charger is inserted or removed
2. USB output channels may power down when charger is connected.
3. USB power supply to one channel may momentarily power down when a device is inserted to the other channel

Given the above, we suggest the following practice for charging your battery

1. Shutdown JetBot (from Jupyter Lab terminal)

    ```bash
    sudo shutdown now
    ```
2. Unplug Jetson Nano and Motor driver from battery pack
3. Insert charger into battery pack
4. Wait for battery to charge
5. Unplug charger from battery pack
6. Plug Jetson Nano and Motor driver back into battery pack

The robot should boot automatically and launch Jupyter notebook.  Sometimes IP address will change, if you have attached the PiOLED it will automatically update and display the new IP address.

## High current shutdown

In some situations, like running intense computation and stalling motors, it is possible to draw enough current to lower
the battery voltage enough to cause the Jetson Nano to shutdown.  This occurrence is rare, and we have only witnessed
it when running the Jetson Nano in MAX-N (high power) mode.  To prevent this, we recommend placing the Jetson Nano in
5W mode by calling the following from a terminal

```bash
sudo nvpmodel -m1
```

You can check the current power mode by calling

```bash
nvpmodel -q
```