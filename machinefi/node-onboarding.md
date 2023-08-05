# Layer-2 Nodes Onboarding

## **W3bStream: IoTeX's Layer-2 Implementation for MachineFi**

W3bStream stands as the pioneering implementation of Layer-2 envisioned in IoTeX's transformative MachineFi vision. Designed to revolutionize the financialization of machines, W3bStream serves as the crucial bridge that connects Layer-1 blockchain to real-world IoT devices.

{% hint style="success" %}
Learn more about W3bstream at [**docs.w3bstream.com**](https://docs.w3bstream.com/introduction/readme)
{% endhint %}

## W3bstream Node Onboarding Process&#x20;

To onboard a W3bStream node into the IoTeX MachineFi ecosystem, the node operator undergoes a simple yet essential process. The operator begins by creating a "**Decentralized Identit**<mark style="color:purple;">**y**</mark>" (DID) on the IoTeX blockchain and **staking a specified amount of IOTX** tokens. This step establishes a secure and trustless identity for the node within the network.

Upon executing the official [W3bStream docker image](https://w3bstream.com) on the node for the first time, the operator is prompted to provide their DID. **The W3bStream node** then autonomously generates **its own DID and corresponding DID document**, both of which are recorded on the blockchain. The DID document contains crucial information, including the public key of the W3bStream node and its service endpoint (such as an MQTT endpoint).

The node operator holds control over the node's DID document, enabling them to **manage and regulate the node's activities securely**. Once the onboarding process is completed successfully, the W3bStream node transitions to the '**Idle**' state, signifying its readiness to serve MachineFi dApps.

By streamlining the onboarding process and establishing decentralized identities for Layer-2 nodes, IoTeX empowers the W3bStream nodes to actively participate in the MachineFi ecosystem, contributing to the financialization of machines and fostering innovative applications for a connected world.
