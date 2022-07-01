# Data - Proofs - APIs

### Data Sending

Depending on the requirements of a Dapp, the client application encodes the raw data collected from the Web2-based IoT system into a data object and signs it using the private key. The signed data object is then sent to a W3bStream node endpoint via a wireless communication channel (i.e., HTTP, MQTT, etc.) for further processing.

### Proof Generating

Depending on the rewarding mechanism in a Dapp, the W3bStream node(s) needs to validate whether the raw data satisfies the condition(s) specified by the Dapp. To this end, the W3bStream node(s) verifies the digital signature of the received data object. \
\
If the verification succeeds, the W3bStream node(s) decodes the data object to obtain the raw data, checks the condition(s), and generates the corresponding proof. \
\
The proof is then sent to a Dapp smart contract. \
\
**Note** that the W3bStream node(s) should be customized in order to support a specific Dapp.

### W3bStream Subgraph APIs

The W3bStream node implements the Graph protocol for indexing and querying data from the IoTeX blockchain. The subgraph can expose the following APIs:

* `rewardClaim(walletAddr, previousTime, currentTime)` – Claim tokens from the previous claim time to the current one
* `getAddress(searchCondition)` – Get all the blockchain wallet addresses that satisfy a specific condition
