# Build on Linux/macOS

* [Install Dependencies](https://docs.iotex.io/developer/hardware/pebble-build-linux.html#install-dependencies)
* [Install ARM Compiler Toolchain](https://docs.iotex.io/developer/hardware/pebble-build-linux.html#install-arm-compiler-toolchain)
* [Install the Nordic SDK](https://docs.iotex.io/developer/hardware/pebble-build-linux.html#install-the-nordic-sdk)
* [Clone the Pebble-Firmware IoTeX repository:](https://docs.iotex.io/developer/hardware/pebble-build-linux.html#clone-the-pebble-firmware-iotex-repository)
* [Compile Project with Command Line](https://docs.iotex.io/developer/hardware/pebble-build-linux.html#compile-project-with-command-line)

### Install Dependencies <a href="#install-dependencies" id="install-dependencies"></a>

First, make sure you have current versions for the following tools:

```bash
cmake --version # must be >= 3.13.1
dtc --version # must be >= 1.4.6
python --version # bust be >= 3.6
```

Follow the instruction below to install the required tools:

{% tabs %}
{% tab title="Linux" %}
If required, update your system:

```bash
sudo apt-get update
sudo apt-get upgrade
```

Install the required tools

```bash
sudo apt-get install --no-install-recommends git cmake ninja-build gperf ccache dfu-util device-tree-compiler wget python3-dev python3-pip python3-setuptools python3-tk python3-wheel xz-utils file make gcc gcc-multilib g++-multilib libsdl2-dev
```
{% endtab %}

{% tab title="macOS" %}
If it is not installed in your system, install [Homebrew (opens new window)](https://brew.sh/)by following instructions on the Homebrew:

```
 $ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

Install required tools:

```
brew install cmake ninja gperf ccache dfu-util dtc python3
```
{% endtab %}
{% endtabs %}

### Install the ARM Compiler Toolchain <a href="#install-arm-compiler-toolchain" id="install-arm-compiler-toolchain"></a>

Download the ARM embedded compiler toolchain

{% tabs %}
{% tab title="Linux" %}
```bash
cd ~
# Download the package
wget https://armkeil.blob.core.windows.net/developer/Files/downloads/gnu-rm/9-2020q2/gcc-arm-none-eabi-9-2020-q2-update-x86_64-linux.tar.bz2
# Extract
tar -jxvf gcc-arm-none-eabi-9-2020-q2-update-x86_64-linux.tar.bz2
# Rename the directory to ~\gnuarmemb
mv gcc-arm-none-eabi-9-2020-q2-update gnuarmemb

```


{% endtab %}

{% tab title="macOS" %}
```
cd ~
# Download the package
wget https://armkeil.blob.core.windows.net/developer/Files/downloads/gnu-rm/9-2020q2/gcc-arm-none-eabi-9-2020-q2-update-mac.tar.bz2
# Extract
tar -jxvf gcc-arm-none-eabi-9-2020-q2-update-mac.tar.bz2
# Rename the directory to ~\gnuarmemb
mv gcc-arm-none-eabi-9-2020-q2-update gnuarmemb
```


{% endtab %}
{% endtabs %}

set required environment variables

```bash
# Create ~/.zephyrrc for easy env variables management
echo 'export ZEPHYR_TOOLCHAIN_VARIANT=gnuarmemb' >> ~/.zephyrrc
echo 'export GNUARMEMB_TOOLCHAIN_PATH="~/gnuarmemb"' >> ~/.zephyrrc
```

### Install the Nordic SDK <a href="#install-the-nordic-sdk" id="install-the-nordic-sdk"></a>

the Nordic SDK is managed by the `west`tool, so we first need to install **west**: open a terminal and type

```bash
# Install west
pip3 install --user -U west
# Make sure the `west`executable is in front of your PATH:
echo 'export PATH=~/.local/bin:"$PATH"' >> ~/.bashrc
source ~/.bashrc
# Check that west is correctly installed
west --version

```

In your home directory, create a folder named `ncs`: we will install the SDK there:

```bash
mkdir ~/ncs
cd ~/ncs
# Initialize the folder
west init -m https://github.com/nrfconnect/sdk-nrf --mr v1.3.0
# Download all required repositories
west update
# Export a Zephyr CMake package. This allows CMake to automatically load the boilerplate code required for building nRF Connect SDK applications:
west zephyr-export

```

Install required python dependencies

```bash
pip3 install -r zephyr/scripts/requirements.txt
pip3 install -r nrf/scripts/requirements.txt
pip3 install -r bootloader/mcuboot/scripts/requirements.txt
```

### Clone the Pebble-Firmware IoTeX repository: <a href="#clone-the-pebble-firmware-iotex-repository" id="clone-the-pebble-firmware-iotex-repository"></a>

The pebble-firmware IoTeX repository contains the firmware application source and the board definition file:

```bash
git clone  https://github.com/iotexproject/pebble-firmware-legacy.git
```

Before we can build the firmware we need to replace the default board definition from the nordic SDK with the one for Pebble:

```bash
# Delete the default board definition
rm -rf ~/ncs/nrf/boards/arm/thingy91_nrf9160
# Replace with the one from pebble-firmware
cp -rv ~/pebble-firmware-legacy/nrf/boards/arm/thingy91_nrf9160 ncs/nrf/boards/arm/
```

Before trying to build the project you must set the required environment variables for Zephyr, to do so you can run:

```bash
# Load environment variables for the Zephyr SDK
source ~/ncs/zephyr/zephyr-env.sh
```

Among other things, this will also source your `~/.zephyrrc` where the arm toolchain environment variables are set: you can use this file to add any customization to the environment.

{% hint style="warning" %}
Please notice that the environment variables will be lost if you close your terminal window: run `source ~/ncs/zephyr/zephyr-env.sh` again to get them back
{% endhint %}

The project can then be compiled with the following commands:

```bash
cd ~
# Make sure to remove any previously created build directory
rm -rf build/
# Start the build process
west build -b thingy91_nrf9160ns ~/pebble-firmware-legacy/nrf/applications/asset_tracker/
```

After the project is compiled successfully, you can flash the new Pebble firmware that is available at `~/build/zephyr/app_signed.hex`.

See [how to configure the firmware](https://docs.iotex.io/developer/hardware/pebble-configure) before the build. See [how to flash the firmware](https://docs.iotex.io/developer/hardware/pebble-flash).
