# Ethereum API Compatibility

In addition to the native IoTeX API, any IoTeX node exposes an Ethereum-compatible JSON API: you can point your [Ethereum libraries and tools](../web3-development/) to an IoTeX full-node with the Gateway service enabled, and have them work with the IoTeX blockchain with no changes.

{% embed url="https://ethereum.org/en/developers/docs/apis/json-rpc/#json-rpc-methods" %}

## Chain ID

The `chainID` chain identifier was introduced in [`EIP-155`](https://eips.ethereum.org/EIPS/eip-155#list-of-chain-ids) **to prevent replay attacks between Ethereum-compatible chains**, it is a way to tell chains apart. Subsequent to `EIP-155`, Ethereum was assigned a `chainID` of 1.

In respect of this `EIP`, IoTeX `chainIDs` have been picked as follow:

| Network       | chainID |
| ------------- | ------- |
| IoTeX Mainnet | `4689`  |
| IoTeX Testnet | `4690`  |

## Web3 API endpoints

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

which gives you the following Ethereum address:`0xE584ca6F469c11140Bb9c4617Cb8f373E38C5D46.`

Then you can query the Babel endpoint according to the Ethereum JSON RPC API:

```bash
» curl -X POST -H "Content-Type:application/json" --data '{"id": 1, "jsonrpc": "2.0", "method": "eth_getBalance", "params": ["0xE584ca6F469c11140Bb9c4617Cb8f373E38C5D46", ""]}' https://babel-api.mainnet.iotex.io
{
  "id": 1,
  "jsonrpc": "2.0",
  "result": "0x10f0cf064dd59200000"
}
```

Which returns the balance `0x10f0cf064dd59200000` (hex) for the address, [expressed in Rau units](../basic-concepts/iotx-token.md#iotx-fractions) (i.e. 5000000000000000000000 Rau, equivalent to 5000 \_\_ IOTX).

Check out the official Ethereum JSON-RPC API Documentation at:

{% embed url="https://ethereum.org/en/developers/docs/apis/json-rpc/#json-rpc-methods" %}

## Supported API

Below is the list of Ethereum APIs currently supported by IoTeX nodes. Any other API not listed here should be considered unsupported and it can be requested by submitting an issue to the following repository:

{% embed url="https://github.com/iotexproject/iotex-core/issues" %}

* `eth_accounts`
* `eth_blockNumber`
* `eth_call`
* `eth_chainId`
* `eth_estimateGas`
* `eth_gasPrice`
* `eth_getBalance`
* `eth_getBlockByHash`
* `eth_getBlockByNumber`
* `eth_getBlockTransactionCountByHash`
* `eth_getBlockTransactionCountByNumber`
* `eth_getCode`
* `eth_getFilterChanges`
* `eth_getFilterLogs`
* `eth_getLogs`
* `eth_getStorageAt`
* `eth_getTransactionByBlockHashAndIndex`
* `eth_getTransactionByBlockNumberAndIndex`
* `eth_getTransactionByHash`
* `eth_getTransactionCount`
* `eth_getTransactionReceipt`
* `eth_hashrate`
* `eth_mining`
* `eth_newBlockFilter`
* `eth_newFilter`
* `eth_protocolVersion`
* `eth_sendRawTransaction`
* `eth_syncing`
* `eth_uninstallFilter`
* `net_listening`
* `net_peerCount`
* `net_version`
* `web3_clientVersion`
