# Babel - Ethereum API

Babel is the IoTeX service that wraps an Ethereum-node JSON-RPC API: you can point your [Ethereum libraries and tools](../web3-development/) to a Babel endpoint, and have them work with the IoTeX blockchain with no changes.&#x20;

{% embed url="https://eth.wiki/json-rpc/API#json-rpc-methods" %}
Official Ethereum JSON-RPC API Documentation
{% endembed %}

You can either deploy a _Babel_ service ([available on GitHub](https://github.com/iotexproject/babel-api)) and point it to your own [IoTeX Gateway node](https://github.com/iotexproject/iotex-bootstrap), or you can use the publicly accessible endpoints [listed below](babel-web3-api.md#babel-api-endpoints).&#x20;

## Chain ID

The `chainID` chain identifier was introduced in [`EIP-155`](https://eips.ethereum.org/EIPS/eip-155#list-of-chain-ids) **to prevent replay attacks between Ethereum-compatible chains**, it is a way to tell chains apart. Subsequent to `EIP-155`, Ethereum was assigned a `chainID` of 1.&#x20;

In respect of this `EIP`, IoTeX `chainIDs` have been picked as follow:

| Network       | chainID |
| ------------- | ------- |
| IoTeX Mainnet | `4689`  |
| IoTeX Testnet | `4690`  |

## Babel API endpoints

#### Mainnet

| Endpoint                               | Provider         | More                                                  |
| -------------------------------------- | ---------------- | ----------------------------------------------------- |
| https://babel-api.mainnet.iotex.io     | IoTeX Foundation | [https://iotex.io](https://iotex.io)                  |
| https://babel-api.mainnet.iotex.one    | IoTeX Foundation | [https://iotex.io](https://iotex.io)                  |
| https://iotexrpc.com                   | Ankr             | [https://iotexrpc.com](https://iotexrpc.com)          |
| https://rpc.ankr.com/iotex             | Ankr             | [https://ankr.com](https://ankr.com)                  |
| https://iotex-rpc.gateway.pokt.network | Pocket Network   | [https://www.pokt.network](https://www.pokt.network/) |

**Testnet**

| Endpoint                           | Text             | More                                 |
| ---------------------------------- | ---------------- | ------------------------------------ |
| https://babel-api.testnet.iotex.io | IoTeX Foundation | [https://iotex.io](https://iotex.io) |

**Example**

To get the balance of the IoTeX address `ukzv5m6xnsg3gzaec3shew8nw03cch2x53d6v6` you first convert it into the ethereum address format using ioctl:

```bash
$ ioctl account ethaddr io1ukzv5m6xnsg3gzaec3shew8nw03cch2x53d6v6
io1ukzv5m6xnsg3gzaec3shew8nw03cch2x53d6v6 - 0xE584ca6F469c11140Bb9c4617Cb8f373E38C5D46
```

which gives you the following Ethereum address:`0xE584ca6F469c11140Bb9c4617Cb8f373E38C5D46.`&#x20;

Then you can query the Babel endpoint according to the Ethereum JSON RPC API:&#x20;

```bash
» curl -X POST -H "Content-Type:application/json" --data '{"id": 1, "jsonrpc": "2.0", "method": "eth_getBalance", "params": ["0xE584ca6F469c11140Bb9c4617Cb8f373E38C5D46", ""]}' http://babel-api.mainnet.iotex.io
{
  "id": 1,
  "jsonrpc": "2.0",
  "result": "0x10f0cf064dd59200000"
}
```

Which returns the balance `0x10f0cf064dd59200000` (hex) for the address, [expressed in Rau units](../dapp-development/basic-concepts/iotx-token.md#iotx-fractions) (i.e. 5000000000000000000000 Rau, equivalent to 5000 __ IOTX).

Check out the official Ethereum JSON-RPC API Documentation at:

{% embed url="https://eth.wiki/json-rpc/API#json-rpc-methods" %}
Official Ethereum JSON-RPC API Documentation
{% endembed %}

## Supported API

Below is the list of the currently supported APIs:

* [x] eth\_accounts
* [x] &#x20;eth\_blockNumber
* [x] &#x20;eth\_call
* [x] &#x20;eth\_chainId
* [x] &#x20;eth\_estimateGas
* [x] &#x20;eth\_gasPrice
* [x] &#x20;eth\_getBalance
* [x] &#x20;eth\_getBlockByHash
* [x] &#x20;eth\_getBlockByNumber
* [x] &#x20;eth\_getBlockTransactionCountByHash
* [x] &#x20;eth\_getBlockTransactionCountByNumber
* [x] &#x20;eth\_getCode
* [x] &#x20;eth\_getFilterChanges
* [x] &#x20;eth\_getFilterLogs
* [x] &#x20;eth\_getLogs
* [x] &#x20;eth\_getStorageAt
* [x] &#x20;eth\_getTransactionByBlockHashAndIndex
* [x] &#x20;eth\_getTransactionByBlockNumberAndIndex
* [x] &#x20;eth\_getTransactionByHash
* [x] &#x20;eth\_getTransactionCount
* [x] &#x20;eth\_getTransactionReceipt
* [x] &#x20;eth\_hashrate
* [x] &#x20;eth\_mining
* [x] &#x20;eth\_newBlockFilter
* [x] &#x20;eth\_newFilter
* [x] &#x20;eth\_protocolVersion
* [x] &#x20;eth\_sendRawTransaction
* [x] &#x20;eth\_syncing
* [x] &#x20;eth\_uninstallFilter
* [x] &#x20;net\_listening
* [x] &#x20;net\_peerCount
* [x] &#x20;net\_version
* [x] &#x20;web3\_clientVersion

Additional API methods support can be requested by posting an issue in the GitHub repository below:

{% embed url="https://github.com/iotexproject/iotex-core/issues" %}

