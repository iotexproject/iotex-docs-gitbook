# Build on Windows

hello&#x20;

* [Download and Install nRF Connect for Windows](https://docs.iotex.io/developer/hardware/pebble-build-windows.html#download-and-install-nrf-connect-for-windows)
* [Install the Nordic Toolchain Manager app](https://docs.iotex.io/developer/hardware/pebble-build-windows.html#install-the-nordic-toolchain-manager-app)
* [Download and install the Pebble SDK package](https://docs.iotex.io/developer/hardware/pebble-build-windows.html#download-and-install-the-pebble-sdk-package)
* [Open and configure the Embedded Studio IDE](https://docs.iotex.io/developer/hardware/pebble-build-windows.html#open-and-configure-the-embedded-studio-ide)
* [Build Pebble Application Firmware](https://docs.iotex.io/developer/hardware/pebble-build-windows.html#build-pebble-application-firmware)
  * [Build in Embedded Studio IDE](https://docs.iotex.io/developer/hardware/pebble-build-windows.html#build-in-embedded-studio-ide)
  * [Build from Command Line](https://docs.iotex.io/developer/hardware/pebble-build-windows.html#build-from-command-line)

![](<../../../../../.gitbook/assets/one\_click\_fig6 (1).png>)

The Pebble firmware can be easily configured and built on Windows using _Pebble SDK_: a customized version of the Nordic's nRF Connect SDK. Make sure you have [Git installed ](https://git-scm.com/download/win)in your system before you continue.

### Download and Install nRF Connect for Windows <a href="#download-and-install-nrf-connect-for-windows" id="download-and-install-nrf-connect-for-windows"></a>

First, access the Nordic [nRF Connect download page for Desktop (opens new window)](https://www.nordicsemi.com/Software-and-tools/Development-Tools/nRF-Connect-for-desktop/Download#infotabs)and download the latest version of **nRF Connect for Windows**:

![](../../../../../.gitbook/assets/one\_click\_fig1.png)

Double-click the downloaded executable file (e.g., `nrfconnect-setup-3.6.0-ia32.exe`) and complete the installation.

### Install the Nordic Toolchain Manager app <a href="#install-the-nordic-toolchain-manager-app" id="install-the-nordic-toolchain-manager-app"></a>

Now launch the _nRF Connect_ utility that you just installed, scroll down to **Toolchain Manager** and click the **Install** button to install the app:

![](../../../../../.gitbook/assets/one\_click\_fig2.png)

### Download and install the Pebble SDK package <a href="#download-and-install-the-pebble-sdk-package" id="download-and-install-the-pebble-sdk-package"></a>

Finally, download one of the following Pebble SDK installation packages (please notice that this guide is based on v1.3.0):

[Pebble SDK 1.3.0](https://pebbles-software-release.s3-us-west-1.amazonaws.com/ncs-toolchain-pebble\_v1.3.0-20200618-509f057.zip)\
[Pebble SDK 1.4.0](https://pebbles-software-release.s3-us-west-1.amazonaws.com/ncs-toolchain-pebble\_v1.4.0-20201030-2750604.zip)

and save the file to a known location in your filesystem.

{% hint style="warning" %}
Make sure you have a Github account and that you set up an SSH key for it before you click 'OK' in the next step (check out [this guide (opens new window)](https://docs.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)on how to generate and an SSH key pair for your GitHub account). If you assigned a password to your ssh private key when you generated it, then nRF Connect will ask for this password during the installation.
{% endhint %}

In the **nRF Connect** app, scroll down to the **Toolchain Manager** and click the **Open** button to open the app. In the toolchain manager window, click the _Install package from other source_ link at the bottom:

![](../../../../../.gitbook/assets/one\_click\_fig3.png)

select the file Pebble SDK package that you just downloaded (`ncs-toolchain-pebble_v1.3.0-20200618-509f057.zip`) and click `OK`

### Open and configure the Embedded Studio IDE <a href="#open-and-configure-the-embedded-studio-ide" id="open-and-configure-the-embedded-studio-ide"></a>

Once the SDK installation is completed, `nRF Connect SDK pebble_v1.3.0` will show up in the Toolchain Manager list: Click the **Open IDE** button:

![](../../../../../.gitbook/assets/one\_click\_fig4.png)

The compiler toolchain paths in Embedded Studio should be already set, just make sure they are configured correctly:

* Choose **Options** under the **Tools** menu
* Choose **nRF Connect** on the left side of the "Option" window
* Locate **Directories** section and configure "GNU ARM Embedded Toolchain Directory" and "Zephyr Base" to the corresponding directories, respectively (see the image):

![](../../../../../.gitbook/assets/one\_click\_fig6.png)

### Build the Application Firmware <a href="#build-pebble-application-firmware" id="build-pebble-application-firmware"></a>

#### Build in Embedded Studio IDE <a href="#build-in-embedded-studio-ide" id="build-in-embedded-studio-ide"></a>

In the Embedded Studio IDE and choose **Open nRF Connect SDK Project...** under the **File** menu and configure the paths of **CMakeLists.txt** and **Board Directory**, also set **Board Name** to `thingy91_nrf9160ns`, as shown in the image below (please adapt to your Windows user path):

![](../../../../../.gitbook/assets/one\_click\_fig5.png)

If required, after the project has been generated, you can configure the firmware parameters before the build following the [firmware configuration instructions](configure-the-firmware.md).

Choose **Build Solution** from the **Build** menu to build the firmware: check out the output panel for the compilation output and wait until the end of the compilation process.

At the end of the build process you will find the new Pebble firmware file at:

```
C:\users\<your_username>\ncs\v1.3.0\nrf\applications\asset_tracker\build_thingy91_nrf9160ns\zephyr\app_signed.hex
```

#### Build from Command Line

If you run into any troubles building the firmware application using Embedded Studio IDE, you can try building the firmware using the command line first.

To do so, locate and open the `git-bash.exe` terminal in your SDK folder:

`C:\john\ncs\v1.3.0\toolchain\git-bash.exe`

in the git-bash terminal, move to the Pebble application folder and compile the application:

```bash
cd %userprofile%/ncs/v1.3.0/nrf/applications/asset_tracker
# Make sure to remove any previously created build directory
rmdir /s /q build
# Start the build process
west build -b thingy91_nrf9160ns
```

Using this build command, the project will be generated in the `build` folder, and the firmware file will be built to the `build\zephyr\app_signed.hex` path.

See [how to configure the firmware](https://docs.iotex.io/developer/hardware/pebble-configure) before the build. See [how to flash the firmware](../flashing-the-firmware/).
