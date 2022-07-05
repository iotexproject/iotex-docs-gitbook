# Device Binding

In the proxy-based integration pattern, a Web2-based IoT system manages all the IoT devices, user accounts, and device ownership. \
\
Each IoT device is uniquely identified with a device identifier (`devID`) and a user with a user identifier `uID` might own multiple IoT devices.&#x20;

The purpose of device binding, in this case, is to associate a device’s digital twin identifier (`twinID`) with its owner’s blockchain wallet address.

![ Device Binding for Web2-based IoT Devices](<../../.gitbook/assets/Screen Shot 2022-06-20 at 1.09.36 PM.png>)

To complete the device binding for a Web2-based IoT device, one can use the following steps:

Since legacy IoT devices often rely on centralized third-party services, the [proxy mode](proxy-based-pattern.md) seems to be a natural choice for connecting those devices to W3bStream nodes. For completing the device binding for a traditional IoT device, the following steps can be followed:

1. The client application generates a private/public key pair and derives a machine DID on behalf of the IoT device;
2. The client application sends the machine DID to the user’s blockchain wallet for signature;
3. The client application sends the signature to a W3bStream node that forwards it to the blockchain;
4. Upon successful verification by the smart contract, the owner’s blockchain wallet address binds with the IoT device’s identity.

The above device binding process essentially creates a ‘digital twin’ for an IoT device and binds the identity of the digital twin with a user’s blockchain address. However, it is difficult to differentiate a real IoT device from a simulator in this case and an attacker might create digital twins arbitrarily. Before the client application sends data to the W3bStream node(s), it will first retrieve data from the third-party service and then digitally sign it using the private key of the IoT device’s digital twin.
