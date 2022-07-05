# Device Binding / Unbinding

Device binding, which binds an IoT device’s identity **with its owner’s blockchain address**, is an essential component in W3bStream. After a successful device binding, all the rewards an IoT device earns will be **credited to its owner**’s blockchain wallet. Due to the heterogeneity of IoT devices as well as the lack of standards, the device binding protocol varies a lot in practice. \
\
A high-level description of a decentralized, challenge-response based device binding process is illustrated below:

![Device Binding based on "challenge-response" pattern](<../../.gitbook/assets/image (86).png>)

After logging into the IoTeX [MachineFi portal](https://portal.machinefi.com) using the web3-based approach (i.e. through a Web3 compatible wallet), a user sends a device binding request to a W3bStream node which then registers the request **on the blockchain**. Upon successful registration of the device binding proposal, the W3bStream node sends a **device binding challenge** to the IoT device which then generates a **response** after the user’s confirmation. The device binding response might be verified by a group of W3bStream nodes for reaching consensus or passed to the blockchain for validation directly. Once the verification succeeds, the association of the IoT device’s identity and its owner’s wallet address is recorded on the blockchain. \
\
For unbinding an IoT device, the device owner can simply send a device unbinding request to a W3bStream node. The device unbinding request might be verified by a group of W3bStream nodes for reaching consensus or passed to the blockchain for validation directly. Once the verification succeeds, the IoT device’s ownership is updated to ‘null’.
