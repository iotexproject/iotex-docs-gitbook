# Firmware update

There are two options for you to update the firmware of your Pebble Tracker: OTA (“Over The Air”) Update and Offline Update.

### OTA Firmware Upgrade

If you want to update the firmware over the air, you will need a [working IoT SIM card](quick-start.md#finding-a-sim-card) installed in your Pebble Tracker with enough credit available to download the firmware file. Follow the steps below to start the OTA firmware update:

1. Make sure your SIM card is correctly installed in the SIM card slot of the device
2. Power off your Pebble Tracker by pressing the `Power/Confirm` button and keeping it pressed until the status led flashes green
3. Press and keep pressing the `Up Arrow` button, then press and release the `Power/Confirm` button (while keeping the Up Arrow still pressed).&#x20;
4. Release the up arrow once the device is powered on and you see the message “_<mark style="color:purple;">OTA Firmware Update. Connecting...</mark>_” message on the display
5. Wait for the device to connect to the cellular network and the message “_<mark style="color:purple;">Please choose an app from the portal</mark>_” is displayed
6. Open [portal.machinefi.com](https://portal.machinefi.com) in a Metamask compatible Browser, or directly inside [ioPay mobile](https://iopay.me), and connect to the portal with your MachineFi blockchain account (you can create one by following the [get started guide](quick-start.md))
7. Select the “**App Store**” tab, then locate and open the “**Firmware Upgrade**” app and click the “**Install**” button
8. In the following dialog, select the device you want to upgrade --> ✳️
9. Make sure your Pebble is showing the “_<mark style="color:purple;">Please, choose an app on the portal</mark>_” message on the display, and click the `Next` button
10. Go ahead and click `Next` on the second dialog to trigger firmware upgrade request transaction for your device
11. Confirm the transaction in your wallet
12. Wait for the Pebble tracker to detect the request and start downloading the firmware

{% hint style="success" %}
\-> ✳️ If you own multiple devices, you can identify your devices from the “**Devices**” tab on the MachineFi portal by matching the IMEI number with the one printed on the Pebble box, and the serial number printed on the box with the one printed on the back of the device
{% endhint %}

The download and installation of the firmware may require some time. In some cases, the download can fail due to a network error: this is usually caused by a low cellular signal in your area, especially if your SIM card connects using the NB-IoT band. In this case, you can try again, or just try the offline firmware update method detailed below.

### Offline Firmware Upgrade

Use this method if you don’t have a SIM card yet, or the IoT cellular connection is not strong enough in your area, or just you don’t want to consume data from your IoT data plan.&#x20;

You can perform a firmware upgrade of your Pebble Tracker offline by following the steps below:

#### 1. Download the latest firmware file&#x20;

Please make sure you download the file ending in `.hex`

{% embed url="https://github.com/iotexproject/pebble-apps/releases/tag/v1.0.13-riverrock" %}

#### 4. Install and run Pebble USB Tools

{% tabs %}
{% tab title="macOS" %}
1. Download and install the latest [VCP Drivers](https://www.silabs.com/developers/usb-to-uart-bridge-vcp-drivers) for macOS
2. Download, unzip and run the executable file: [`PebbleUSBTool`](https://drive.google.com/drive/folders/1cQsBcBLBQolIwTY\_41n5lSzmtSZPH83e?usp=share\_link)
{% endtab %}

{% tab title="Windows" %}
1. Download and install the latest [VCP Driver](https://www.silabs.com/developers/usb-to-uart-bridge-vcp-drivers) for Windows
2. Download and install the latest [J-link software](https://www.segger.com/downloads/jlink/) for Windows
3. Unzip and run the executable file: [`PebbleUSBTools.exe`](https://drive.google.com/file/d/1e5bcFnkK9oFWSLqikJicYKMcyYfUKyAg/view?usp=share\_link)
{% endtab %}

{% tab title="Ubuntu" %}
1. Download and unzip [PebbleUSBTools](https://drive.google.com/file/d/1ACW8KLiGJfB7q5t2Kp1YAolxr4oIeml8/view?usp=share\_link)
2. Enter the `PebbleUSBTool` folder
3. Install `pebble-udev_1.0.1-all.deb`
4. `chmod +777 PebbleUSBTools`
5. Reboot your system
6. Inside the PebbleUSBTool folder run `./PebbleUSBTools`
{% endtab %}
{% endtabs %}

#### Restart Pebble in Firmware update mode

Make sure your Pebble battery is charged. Press and keep pressing the `Confirm/Power` button, then use a pin or a SIM card tool to press the hardware reset button (while you keep pressing the `Power` button).

The Pebble should now boot in firmware update mode, with the status led of red color and always on: you can release the `Power` button.&#x20;

{% hint style="warning" %}
You will have about 20 seconds to perform the next steps or the device will auto-restart if no action is taken.
{% endhint %}

#### 3. Connect Pebble to your computer

Use the micro-USB data cable provided with Pebble to connect the device to your computer using a USB port

#### Flash the Firmware

In the Pebble USB Tool, notice when the status bar says that the Pebble is connected:&#x20;

![](<../../../.gitbook/assets/image (104).png>)

then click the “`Flash APP Firmware`” button:

![](<../../../.gitbook/assets/image (84).png>)

Wait for the firmware upgrade to complete. The device will reboot automatically after the operation is completed, and the new firmware will be loaded.
