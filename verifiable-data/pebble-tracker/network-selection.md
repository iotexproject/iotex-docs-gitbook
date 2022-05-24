# Network selection

The default firmware installed on Pebble Tracker wraps sensor readings in an MQTT message and sends one data message every 5 minutes to the IoTeX [Real World Data Oracle](../../layer2/real-world-data-oracle.md) **Mainnet network**.&#x20;

Alternatively, the firmware can be configured to send the data to the testnet oracle network by following the steps below:

1.  **Enter the firmware configuration**

    Power on the device while pressing and keep pressing the down arrow until you see the firmware configuration menu.
2.  **Go to "System Settings"**

    User the up/down arrow buttons to select the "System Settings" menu item to move between menu options. Shortly press the power button to confirm the selection.
3.  **Go to "Select Region"**

    Go to the "Select Region" menu item and press the power button to confirm the selection.
4.  **Select the network**

    Select the menu item that ends by "`- M`" to send the data to the Mainnet network, or select the menu item that ends by "`- T`" to send the data to the Testnet network.
5.  **Reboot the device**

    Use the arrow buttons and the power button to select "Exit" in the menu until you get back to the initial menu, then select "Reboot Pebble."

You can check the currently selected network on the display when Pebble is powered on and while it's connecting to the network:

![Currently selected network](<../../.gitbook/assets/image (24).png>)

To visualize the data collected by your devices, you can use the MachineFi portal. For data sent to the mainnet Oracle network will be available on https://portal.machinefi.com. If you selected the Testnet Network on your device, you should use https://portal-testnet.machinefi.com instead.&#x20;
