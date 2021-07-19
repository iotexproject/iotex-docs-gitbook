# Antenna SDK Overview

"**Antenna"** is the IoTeX native SDK, allowing you to directly interact with a local or remote IoTeX node using a gRPC connection, and is available for the most popular programming languages.  The difference between developing using **Antenna** or [Web3 SDK](../ethereum-copmpatibility/web3.js.md) is that Antenna wraps the full [gRPC Native API](../reference/node-core-api-grpc.md) of the IoTeX protocol and uses the [native representation of IoTeX addresses](../basic-concepts/address-conversion.md#iotex-address-format). 

While IoTeX fully supports the Ethereum API, allowing you to use Web3 tools for dApp development, the fact that IoTeX architecture is more complex than Ethereum's, makes Antenna the necessary choice when you want to make use of IoTeX unique features. For example, "Delegates," "Block Producers," "Staking Transactions," "Buckets," "Voting," etc., are concepts that find no correspondence in Ethereum. Therefore if you want to use these features in your dApp, you won't find them in, e.g., Web3js: in this case, you will have to use Antenna.

[The reference implementation](reference-code/create-an-account.md) is included for each supported language; you can find examples of using these libraries in the [Examples section]().

### Supported Languages <a id="supported-languages"></a>

**antenna-js \(Javascript\):** [**Installation**](antenna-installation/install-antenna-js.md) **\|** [**GitHub**](https://github.com/iotexproject/iotex-antenna)\*\*\*\*

**antenna-java \(java\):** [**Installation**](antenna-installation/antenna-java.md) **\|** [**GitHub**](https://github.com/iotexproject/iotex-antenna-java)\*\*\*\*

**antenna-go \(go lang\):** [**Installation**](antenna-installation/antenna-go.md) **\|** [**GitHub**](https://github.com/iotexproject/iotex-antenna-go)\*\*\*\*

**antenna-swift \(iOS\):** [**Installation**](antenna-installation/antenna-swift.md) **\|** [**GitHub**](https://github.com/iotexproject/iotex-antenna-swift)\*\*\*\*

**antenna-embedded \(C\):** [**Installation**](antenna-installation/antenna-embedded.md) **\|** [**GitHub**](https://github.com/iotexproject/iotex-antenna-embedded)\*\*\*\*

### Features <a id="features"></a>

**Crypto**  
This module provides crypto functions to generate public/private keys, sign transactions and data, and other cryptographic utility functions.

**RPC-Methods**  
This module allows calling any RPC-Method provided by an IoTeX Blockchain Gateway.

**Account**  
This Class provides functions to create and manage blockchain accounts.

**Action**  
This module allows to create and manage blockchain actions.

**Contract**  
This class allows interaction with contracts deployed on the IoTeX Blockchain, given the contract address and the ABI.

**XRC20**  
This module allows to send, receive and query wallets for XRC20 tokens deployed on the IoTeX Blockchain.

