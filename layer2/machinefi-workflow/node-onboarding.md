# Node Onboarding

For onboarding a W3bStream node, the node operator needs to **create a DID** (_"Decentralized Identity"_) on the IoTeX blockchain and **stake** a certain amount of IOTX tokens.&#x20;

Once the official **W3bStream docker image** is executed on the node for the first time, it will ask the node operator for his/her DID.&#x20;

Moreover, the **node will create its own DID** and the corresponding DID document on the blockchain. The DID document contains information such as the public key of the W3bStream node as well as its service endpoint (i.e., an MQTT endpoint).&#x20;

The node operator will be the **controller** of the node DID document.

After completing the onboarding process, the W3bStream node goes to the ‘_Idle_’ state and is ready for serving MachineFi Dapps.  &#x20;
