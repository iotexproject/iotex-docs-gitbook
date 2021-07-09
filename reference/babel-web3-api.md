# Babel - Web3 API

Babel is the IoTeX service that wraps an Ethereum-node JSON-RPC API: you can point your web3 [Ethereum clients and tools]() to a Babel endpoint, and have them work with the IoTeX blockchain with no changes. 

{% embed url="https://eth.wiki/json-rpc/API\#json-rpc-methods" caption="Official Ethereum JSON-RPC API Documentation" %}

## Access the Babel API

You can deploy your own Babel service [available on GitHub](https://github.com/iotexproject/babel-api), or you can use the publicly accessible endpoints  below:

#### Mainnet

| Parameter | Value |
| :--- | :--- |
| RPC URL | [`https://babel-api.mainnet.iotex.io`](https://babel-api.mainnet.iotex.io) |
| Chain ID | `4689` |
| Explorer URL | [`https://iotexscan.io`](https://iotexscan.io) |

**Testnet**

| **Parameter** | Value |
| :--- | :--- |
| RPC URL  | [`https://babel-api.testnet.iotex.io`](%20https://babel-api.testnet.iotex.io) |
| Chain ID | `4690` |
| Explorer URL | [`https://testnet.iotex.io`](https://testnet.iotex.io) |

**Example**

To get the balance of the IoTeX address `ukzv5m6xnsg3gzaec3shew8nw03cch2x53d6v6` you first convert it into the ethereum address format using ioctl:

```bash
$ ioctl account ethaddr io1ukzv5m6xnsg3gzaec3shew8nw03cch2x53d6v6
io1ukzv5m6xnsg3gzaec3shew8nw03cch2x53d6v6 - 0xE584ca6F469c11140Bb9c4617Cb8f373E38C5D46
```

which gives you the following Ethereum address:`0xE584ca6F469c11140Bb9c4617Cb8f373E38C5D46.` 

Then you can query the Babel endpoint according to the Ethereum JSON RPC API: 

```bash
» curl -X POST -H "Content-Type:application/json" --data '{"id": 1, "jsonrpc": "2.0", "method": "eth_getBalance", "params": ["0xE584ca6F469c11140Bb9c4617Cb8f373E38C5D46", ""]}' http://babel-api.mainnet.iotex.io
{
  "id": 1,
  "jsonrpc": "2.0",
  "result": "0x10f0cf064dd59200000"
}
```

Which returns the balance `0x10f0cf064dd59200000` \(hex\) for the address, [expressed in Rau units](../basic-concepts/iotx-token.md#iotx-fractions) \(i.e. 5000000000000000000000 Rau, equivalent to 5000 __IOTX\).

Check out the official Ethereum JSON-RPC API Documentation at:

{% embed url="https://eth.wiki/json-rpc/API\#json-rpc-methods" caption="Official Ethereum JSON-RPC API Documentation" %}

## Supported API

Below is the list of the currently supported APIs:

* [x] eth\_chainId
* [x] eth\_blockNumber
* [x] eth\_getBlockByNumber
* [x] eth\_getBalance 
* [x] eth\_gasPrice 
* [x] eth\_getTransactionCount
* [x] eth\_sendRawTransaction
* [x] eth\_call
* [x] eth\_estimateGas 
* [x] eth\_getCode 
* [x] eth\_getTransactionReceipt 
* [x] eth\_protocolVersion 
* [x] eth\_syncing 
* [x] eth\_getBlockTransactionCountByHash 
* [x] eth\_getBlockTransactionCountByNumber 
* [x] eth\_getBlockByHash 
* [x] eth\_getTransactionByHash 
* [x] eth\_getTransactionByBlockHashAndIndex 
* [x] eth\_getTransactionByBlockNumberAndIndex 
* [x] eth\_getLogs
* [x] net\_version 
* [x] net\_peerCount 
* [x] net\_listening 
* [x] web3\_clientVersion 
* [ ] getpeers 
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
* [ ] shh\_newIdentity 
* [ ] shh\_hasIdentity 
* [ ] shh\_newGroup 
* [ ] shh\_addToGroup 
* [ ] shh\_newFilter 
* [ ] shh\_uninstallFilter 
* [ ] shh\_getFilterChanges 
* [ ] shh\_getMessages

