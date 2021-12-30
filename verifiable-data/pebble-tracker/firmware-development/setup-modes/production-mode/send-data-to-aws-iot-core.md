# Send data to AWS IoT Core

This document describes the process for connecting Pebble with the AWS IoT Core and validating that the connection has been established successfully. You need to [configure an AWS IoT Policy and a _Thing_](configure-aws-iot-core.md), make sure you downloaded the AWS cryptographic certificates for that _Thing_ when you created it on AWS, and take note of the AWS IoT device data endpoint (you can find the endpoint in the AWS IoT console on the _Thing_'s details page, it should look similar to `a3qjEXAMPLEffp-ats.iot.us-west-2.amazonaws.com`).

### Update the Credentials in the Firmware <a href="#update-the-cerdentials-in-the-firmware" id="update-the-cerdentials-in-the-firmware"></a>

In order for Pebble to send data to AWS we need to update the firmware to use the certificates we downloaded from AWS for our _Thing_: see the [Develop and Build the Firmware](../../develop-and-build-the-firmware/) to learn how to configure your system to build and flash the Pebble firmware.

Edit the firmware source file `certificate.h` located at `nrf\applications\asset`_`tracker\src\certificates.h`, and replace the content for the macros 'NRF\_CLOUD\_CLIENT\_PRIVATE\_KEY', 'NRF\_CLOUD\_CLIENT\_PUBLIC\_CERTIFICATE', and 'NRF\_CLOUD\_CA\_CERTIFICATE' with the_ AWS _Thing_ private key (i.e. `xxx-private.pem.key`), public certificate (i.e. `xxx-certificate.pem.crt`), and the AWS Root certificate (i.e. `AmazonRootCA1.pem`), respectively.

![](http://docs-old.iotex.io/img/developer/pebble\_certificate\_string.png)

Make sure that you edited the macros correctly (see the image above), adding the new-line character `\n`at the end of each line, without modifying, adding or deleting any character of the certificates.

### Configure the Pebble firmware to use the AWS certificate <a href="#configure-the-firmware-to-use-the-aws-certificate" id="configure-the-firmware-to-use-the-aws-certificate"></a>

To instruct the firmware to actually transfer the new certificates provided in `certificate.h` into the modem, in the firmware configuration locate the item:

`Asset Tracker -> Use provisioned certificates`&#x20;

and **uncheck** it, then locate the item:&#x20;

`Zephyr Kernel -> Modules -> Nordic nRF Connect -> Libraries -> nRF9160 modem key management library`&#x20;

and **enable it.**

Check out [how to configure the firmware](../../develop-and-build-the-firmware/configure-the-firmware.md) for instructions on how to run the firmware configuration tool. You can use the search functionality to quickly locate the setting you are looking for.

### Configure the AWS endpoint in Pebble <a href="#configure-the-aws-endpoint-in-pebble" id="configure-the-aws-endpoint-in-pebble"></a>

There is one last step to make before we can finally build the new firmware: we must set the endpoint of our AWS _Thing_ where the Pebble should send the data to. So, in the firmware configuration locate the item:&#x20;

`Asset Tracker -> MQTT_BROKER_HOSTNAME` &#x20;

set it to your AWS _Thing_ endpoint, then locate the item

`Asset Tracker -> MQTT_BROKER_PORT`&#x20;

set it to `8883` , and save the configuration.

Check out [how to configure the firmware](../../develop-and-build-the-firmware/configure-the-firmware.md) for instructions on how to run the firmware configuration tool.

### Build and flash the modified firmware <a href="#build-and-flash-the-modified-firmware" id="build-and-flash-the-modified-firmware"></a>

Finally, you can [Compile the firmware](../../develop-and-build-the-firmware/) and [flash it](../../flashing-the-firmware/) into the Pebble.

### Validate the connection in AWS IoT <a href="#validate-the-connection-in-aws-iot" id="validate-the-connection-in-aws-iot"></a>

In your AWS IoT console choose **test** in left menu and specify the **Subscription topic** to be `device/nrf-XXXXXXXXXXXXXXX/data`, where `XXXXXXXXXXXXXXX` is the unique 15-digit IMEI number of your Pebble modem (you can find this number printed on a lable included in your Pebble box, also it's reported on the device serial port log output).

![](http://docs-old.iotex.io/img/developer/pebble\_aws\_iot\_test.png)

If the connection between Pebble and AWS has been established correctly, after clicking the **Subscribe to topic** button you will see the json messages incoming (by default, one every 30s) into the AWS test console.
