# Configure your Pebble

The Pebble Configuration Tool is a desktop application designed to modify the configuration settings of your PebbleTracker and to update the device with new firmware.

<figure><img src="../../../.gitbook/assets/image (88).png" alt=""><figcaption></figcaption></figure>

## Download Pebble Configuration Tool

The tool is compatible with both MacOS and Windows. You can download it using the following link:

{% embed url="https://drive.google.com/drive/folders/1ll5ngUwvyORRkH8hBPCd0Sf6bDub18zh?usp=drive_link" %}
Download Pebble Configuration Tool
{% endembed %}

## **Installation and Setup Guide**

### **For Users**

1. **Unzip the Folder:** Locate the downloaded zip file and extract its contents.
2. **Edit Configuration:**
   * Modify the `config.pbi` file as necessary to meet your needs, or replace it with a configuration file downloaded from a project to which you intend to contribute data.
3. **Launch the Tool:** Open the Pebble Configuration Tool and follow the instructions to apply the configuration.

**For macOS Users:**

Make sure you move the `config.pbi` file into the application's directory at `PebbleConfigTool_MacOS.app/Contents/MacOS` before you launch the tool.

## **For Developers**

**Custom Configuration for Projects:**

* If you are developing a product that utilizes trusted data from Pebble Tracker owners, customize the `pebble.pbi` configuration file to suit your project's specific requirements. You can then bundle this customized configuration file with the executable of the Pebble Configuration Tool.
* Distribute this bundled version to your users, enabling them to configure their devices easily to transmit the correct data to your project.

**Simplified User Experience:**

* The Pebble Configuration Tool will automatically detect and load any `pebble.pbi` file present in the executable's directory. In this case, users will see a "HOME" tab displaying your project's description and link according to your `pebble.pbi` content, allowing them to configure their device with just one click.
* MacOS: Make sure you move the `config.pbi` file into the application's directory at `PebbleConfigTool_MacOS.app/Contents/MacOS` when preparing the bundled tool.
