# Configure the firmware

If required, firmware parameters (e.g. MQTT parameters) can be customized before building a new image. You can configure the firmware both from inside Embedded Studio IDE or from command line. The most common settings you may want to configure are the following:

**Enable/Disable GPS**\
`Asset Tracker > GPS > GPS Device`

**MQTT Broker url**\
`Asset Tracker > IoTeX Hosted MQTT broker hostname`

**Network mode (NB-IoT/LTE-M)**\
`Zephyr Kernel > Modules > Nordic nRF Connect > Libraries > nRF91 LTE Link control library > Select network mode`

#### Configure the firmware in Embedded Studio <a href="#configure-the-firmware-in-embedded-studio" id="configure-the-firmware-in-embedded-studio"></a>

From the Embedded Studio, before starting the build process, choose **Configure nRF Connect SDK Project** in the **Project** menu, and choose **menuconfig** in the pop-up window.

You can use the search box to quickly locate te parameters you want to customize, e.g. and search "mqtt" to customize MQTT specific parameters:

![](../../../../.gitbook/assets/firmware\_fig8.png)

#### Configure the firmware from command line <a href="#configure-the-firmware-from-command-line" id="configure-the-firmware-from-command-line"></a>

From command line, you can just run the following command to start the configuration menu:

{% tabs %}
{% tab title="Windows" %}
```bash
# Move into the firmware app folder
cd %userprofile%/ncs/v1.3.0/nrf/applications/asset_tracker
# Optionally, delete the old build folder to start from default configuration
rmdir build /S /Q
# Start the configuration tool
west build -t menuconfig -b thingy91_nrf9160ns
```


{% endtab %}

{% tab title="Linux/macOS" %}
```bash
cd ~
# Optionally, delete the old build folder to start from default configuration
rmdir -rf build
# Start the command line configuration tool
west build -t menuconfig -b thingy91_nrf9160ns ~/pebble-firmware/nrf/applications/asset_tracker/

```
{% endtab %}
{% endtabs %}

The command line configuration tool will show up:

![Command line configuration tool](<../../../../.gitbook/assets/image (14).png>)

You can type the "/" character to quickly search a specific configuration item by name.
