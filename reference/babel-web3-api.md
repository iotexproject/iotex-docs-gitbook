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

| Endpoint                            | Provider         | More                                                 |
| ----------------------------------- | ---------------- | ---------------------------------------------------- |
| https://babel-api.mainnet.iotex.io  | IoTeX Foundation | [https://iotex.io](https://iotex.io)                 |
| https://babel-api.mainnet.iotex.one | IoTeX Foundation | [https://iotex.io](https://iotex.io)                 |
| https://rpc.ankr.com/iotex          | Ankr             | [https://ankr.com](https://ankr.com)                 |
| https://pokt-api.iotex.io           | Pocket Network   | [https://www.pokt.network](https://www.pokt.network) |

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

Which returns the balance `0x10f0cf064dd59200000` (hex) for the address, [expressed in Rau units](../basic-concepts/iotx-token.md#iotx-fractions) (i.e. 5000000000000000000000 Rau, equivalent to 5000 __ IOTX).

Check out the official Ethereum JSON-RPC API Documentation at:

{% embed url="https://eth.wiki/json-rpc/API#json-rpc-methods" %}
Official Ethereum JSON-RPC API Documentation
{% endembed %}

## Supported API

Below is the list of the currently supported APIs:

* [x] eth\_chainId
* [x] eth\_blockNumber
* [x] eth\_getBlockByNumber
* [x] eth\_getBalance&#x20;
* [x] eth\_gasPrice&#x20;
* [x] eth\_getTransactionCount
* [x] eth\_sendRawTransaction
* [x] eth\_call
* [x] eth\_estimateGas&#x20;
* [x] eth\_getCode&#x20;
* [x] eth\_getTransactionReceipt&#x20;
* [x] eth\_protocolVersion&#x20;
* [x] eth\_syncing&#x20;
* [x] eth\_getBlockTransactionCountByHash&#x20;
* [x] eth\_getBlockTransactionCountByNumber&#x20;
* [x] eth\_getBlockByHash&#x20;
* [x] eth\_getTransactionByHash&#x20;
* [x] eth\_getTransactionByBlockHashAndIndex&#x20;
* [x] eth\_getTransactionByBlockNumberAndIndex&#x20;
* [x] eth\_getLogs
* [x] net\_version&#x20;
* [x] net\_peerCount&#x20;
* [x] net\_listening&#x20;
* [x] web3\_clientVersion&#x20;
* [ ] getpeers&#x20;
* [ ] eth\_coinbase
* [ ] eth\_mining
* [ ] eth\_hashrate
* [ ] eth\_accounts
* [ ] eth\_getStorageAt
* [ ] eth\_getUncleCountByBlockHash
* [ ] eth\_getUncleCountByBlockNumber
* [ ] eth\_sign
* [ ] eth\_signTransaction
* [ ] eth\_sendTransaction
* [ ] eth\_getUncleByBlockHashAndIndex
* [ ] eth\_getUncleByBlockNumberAndIndex
* [ ] eth\_newFilter
* [ ] eth\_newBlockFilter
* [ ] eth\_newPendingTransactionFilter
* [ ] eth\_uninstallFilter
* [ ] eth\_getFilterChanges
* [ ] eth\_getFilterLogs
* [ ] eth\_getWork
* [ ] eth\_submitWork
* [ ] eth\_submitHashrate
* [ ] eth\_pendingTransactions
* [ ] db\_putString
* [ ] db\_getString
* [ ] db\_putHex
* [ ] db\_getHex
* [ ] shh\_post
* [ ] shh\_version
* [ ] shh\_newIdentity&#x20;
* [ ] shh\_hasIdentity&#x20;
* [ ] shh\_newGroup&#x20;
* [ ] shh\_addToGroup&#x20;
* [ ] shh\_newFilter&#x20;
* [ ] shh\_uninstallFilter&#x20;
* [ ] shh\_getFilterChanges&#x20;
* [ ] shh\_getMessages
