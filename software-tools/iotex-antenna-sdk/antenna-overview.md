# Overview

_**Antenna**_ is the IoTeX official SDK that allows you to interact with a local or remote IoTeX blockchain node using a gRPC connection. With Antenna you have all that you need to **fetch informations** from the blockchain: current network status, wallets balance or transaction details can be easily obtainted with the functions provided.

If your application involves **sending blockchain actions**, from IOTX transfers and smart contract calls, to **XRC20 tokens** management and direct gRPC API calls you are all covered!

[Reference implementation](reference-code/create-an-account.md) is included for each supported language, and examples of how to use these libraries can be found in the [Examples section](examples.md).

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
This modure allows to call any RPC-Method provided by an IoTeX Blockchain Gateway.

**Account**  
This Class provides functions to create and manage blockchain accounts

**Action**  
This module allows to create and manage blockchain actions

**Contract**  
This class allows to interact with contract deployed on the IoTeX Blockchain, given the contract address and the ABI

**XRC20**  
This module allows to send, receive and query wallets for XRC20 tokens deployed on the IoTeX Blockchain.

