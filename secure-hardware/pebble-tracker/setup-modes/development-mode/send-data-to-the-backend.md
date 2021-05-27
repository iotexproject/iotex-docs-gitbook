# Send data to the backend

### Prerequisites <a id="prerequisites"></a>

1. Make sure you have the Pebble Firmware development environment configured on your machine: see the **Develop and Build the Firmware** documentation for [Windows](../../develop-and-build-the-firmware/build-on-windows.md) or [Linux/MacOs](../../develop-and-build-the-firmware/build-on-linux-macos.md).
2. Make sure you can access your Pebble Backend service **on a public ip address**: you can deploy your own Backend server by following [the Pebble Backend Configuration](deploy-the-backend-service.md) guide.

{% hint style="info" %}
If you don't have access to a cloud server, you can still deploy the backend on a server in your local network, and use tools like [ngrok ](https://ngrok.com/)or [no-ip ](https://www.noip.com/)to make it publicly accessible.
{% endhint %}

### Configure the Firmware to connect to backend <a id="configure-the-firmware-to-connect-to-backend"></a>

In order to have Pebble data sent to the IoTeX Pebble Backend you only need to configure the `MQTT_BROKER_HOSTNAME` setting in the firmware configuration with the ip address or the url of the pebble backend you want to use \(set it to `trypebble.io` if you want to use the IoTeX Public Backend, this is the factory default\).

1. Follow the \[Pebble Firmware Configuration\]\[pebble-firmware-configure\] guide to start the firmware configuration tool, find the `MQTT_BROKER_HOSTNAME` setting and configure it with your backend url. Also find the `MQTT_BROKER_PORT` setting and make sure it's configured with the correct hmq port - 1884 is the default\)
2. Save the configuration and build the firmware \(see instructions for [Windows](../../develop-and-build-the-firmware/build-on-windows.md) or [Linux/MacOS](../../develop-and-build-the-firmware/build-on-linux-macos.md)\)
3. [Flash the firmware](../../flashing-the-firmware/) in your Pebble

### Visualize the data <a id="visualize-the-data"></a>

Once your device is restarted and connected to the Internet, it will immediately start sending data to the IoTeX Backend: if you deployed your own Backend server, please make sure that it's accessible from a public ip address, and that the ports 1884 and 8080 are open for the MQTT broker and Thingsboard services respectively.

Access the backend Thingsboard at [trypebble.io ](http://trypebble.io/)\(or your custom backend url on port 8080\) and use the default username and password: 

**Username**: `tenant@thingsboard.org` **Password**: `tenant`.

![](http://docs-old.iotex.io/img/developer/pebble-backend/thingsboard-login.png)

In the navigation panel, click on **devices**: you should see your Pebble among the listed devices, with label `nrf-...` followed by the IMEI number:

![](http://docs-old.iotex.io/img/developer/pebble-backend/thingsboard-device.png)

In the navigation panel, click on **dashboards** and select the Pebble Tracked dashboard to see the incoming data:

![](http://docs-old.iotex.io/img/developer/pebble-backend/thingsboard-dashboard.png)

### Configure Data Collection <a id="configure-data-collection"></a>

Inside the Dashboard you can send MQTT messages to configure Pebble using the `Config Me` button: in the configuration dialog you can enable/disable each measurement, as well as change the data upload interval. Click `OK` button to send the configuration: the new settings will be enabled as soon as the message reaches the board:

![](http://docs-old.iotex.io/img/developer/pebble-backend/thingsboard-config-me.png)

### Find your Pebble <a id="find-your-pebble"></a>

The `Beep me`button can be used to make Pebble play a sound: click the `Beep Me` button, then click `OK`: after a few second a "beep" sound will be emitted by the onboard buzzer:

![](http://docs-old.iotex.io/img/developer/pebble-backend/thingsboard-beep-me.png)

