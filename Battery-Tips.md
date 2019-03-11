This page has tips related to battery charging and usage for [this battery](https://amzn.to/2WRcIUe).

### Battery caveats

* Outputs will momentarily power down when charger is inserted or removed
* Outputs may power down when charger is connected.

### Best charging practice
Given the above battery caveats, we suggest the following practice for charging your battery

1. Shutdown JetBot (from Jupyter Lab terminal)

    ```bash
    sudo shutdown now
    ```
2. Unplug Jetson Nano and Motor driver from battery pack
3. Insert charger into battery pack
4. Wait for battery to charge
5. Unplug charger from battery pack
6. Plug Jetson Nano and Motor driver back into battery pack

### Prevent high current shutdown

In high power mode, it is possible to draw more current than the battery can supply.  To prevent this:

1. Select 5W power mode 

    ```bash
    sudo nvpmodel -m1
    ```
2. Confirm power mode

    ```bash
    nvpmodel -q
    ```