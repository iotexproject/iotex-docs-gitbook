# Babel - Web3 API

Babel is the IoTeX service that wraps an Ethereum-node JSON-RPC API: you can point your web3 [Ethereum libraries and tools](../web3-development/) to a Babel endpoint, and have them work with the IoTeX blockchain with no changes. 

{% embed url="https://eth.wiki/json-rpc/API#json-rpc-methods" %}
Official Ethereum JSON-RPC API Documentation
{% endembed %}

## Access the Babel API

You can deploy your own Babel service [available on GitHub](https://github.com/iotexproject/babel-api), or you can use the publicly accessible endpoints  below:

#### Mainnet

| Parameter    | Value                                                                      |
| ------------ | -------------------------------------------------------------------------- |
| RPC URL      | [`https://babel-api.mainnet.iotex.io`](https://babel-api.mainnet.iotex.io) |
| Chain ID     | `4689`                                                                     |
| Explorer URL | [`https://iotexscan.io`](https://iotexscan.io)                             |

**Testnet**

| **Parameter** | Value                                                                      |
| ------------- | -------------------------------------------------------------------------- |
| RPC URL       | [`https://babel-api.testnet.iotex.io`](https://babel-api.testnet.iotex.io) |
| Chain ID      | `4690`                                                                     |
| Explorer URL  | [`https://testnet.iotex.io`](https://testnet.iotex.io)                     |

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

Which returns the balance `0x10f0cf064dd59200000` (hex) for the address, [expressed in Rau units](../basic-concepts/iotx-token.md#iotx-fractions) (i.e. 5000000000000000000000 Rau, equivalent to 5000_ _IOTX).

Check out the official Ethereum JSON-RPC API Documentation at:

{% embed url="https://eth.wiki/json-rpc/API#json-rpc-methods" %}
Official Ethereum JSON-RPC API Documentation
{% endembed %}

## Supported API

Below is the list of the currently supported APIs:

* [x] eth_chainId
* [x] eth_blockNumber
* [x] eth_getBlockByNumber
* [x] eth_getBalance 
* [x] eth_gasPrice 
* [x] eth_getTransactionCount
* [x] eth_sendRawTransaction
* [x] eth_call
* [x] eth_estimateGas 
* [x] eth_getCode 
* [x] eth_getTransactionReceipt 
* [x] eth_protocolVersion 
* [x] eth_syncing 
* [x] eth_getBlockTransactionCountByHash 
* [x] eth_getBlockTransactionCountByNumber 
* [x] eth_getBlockByHash 
* [x] eth_getTransactionByHash 
* [x] eth_getTransactionByBlockHashAndIndex 
* [x] eth_getTransactionByBlockNumberAndIndex 
* [x] eth_getLogs
* [x] net_version 
* [x] net_peerCount 
* [x] net_listening 
* [x] web3\_clientVersion 
* [ ] getpeers 
* [ ] eth_coinbase
* [ ] eth_mining
* [ ] eth_hashrate
* [ ] eth_accounts
* [ ] eth_getStorageAt
* [ ] eth_getUncleCountByBlockHash
* [ ] eth_getUncleCountByBlockNumber
* [ ] eth_sign
* [ ] eth_signTransaction
* [ ] eth_sendTransaction
* [ ] eth_getUncleByBlockHashAndIndex
* [ ] eth_getUncleByBlockNumberAndIndex
* [ ] eth_newFilter
* [ ] eth_newBlockFilter
* [ ] eth_newPendingTransactionFilter
* [ ] eth_uninstallFilter
* [ ] eth_getFilterChanges
* [ ] eth_getFilterLogs
* [ ] eth_getWork
* [ ] eth_submitWork
* [ ] eth_submitHashrate
* [ ] eth_pendingTransactions
* [ ] db_putString
* [ ] db_getString
* [ ] db_putHex
* [ ] db_getHex
* [ ] shh_post
* [ ] shh_version
* [ ] shh_newIdentity 
* [ ] shh_hasIdentity 
* [ ] shh_newGroup 
* [ ] shh_addToGroup 
* [ ] shh_newFilter 
* [ ] shh_uninstallFilter 
* [ ] shh_getFilterChanges 
* [ ] shh_getMessages
