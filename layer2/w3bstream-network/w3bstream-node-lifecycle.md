# W3bStream Node Lifecycle

The W3bStream framework incentivizes communities to run nodes for supporting the growth of **MachineFi Dapps** in the IoTeX ecosystem. Depending on the requirements of a Dapp, a certain number of W3bStream nodes **might be employed** to serve the Dapp.

![ Lifecycle of a W3bStream Node](<../../.gitbook/assets/Screen Shot 2022-06-22 at 5.10.04 PM.png>)

Any community member who is interested in operating a W3bStream node should provision a virtual machine on the cloud or set up a local server. After downloading and running the official **W3bStream docker image**, the node is in the ‘_Idle_’ state. Once a node operator signs up for a Dapp and loads the business logic module (i.e., a **Wasm** module), the node goes to the ‘_Ready_’ state. Whenever the required number of W3bStream nodes are online, all of them go to the ‘_Busy_’ state and start serving the Dapp. If a node operator decides to leave the current Dapp, the W3bStream node becomes ‘Idle’ again and is able to serve other Dapps. The states of all the W3bStream nodes are managed **by a smart contract** on the blockchain.&#x20;
