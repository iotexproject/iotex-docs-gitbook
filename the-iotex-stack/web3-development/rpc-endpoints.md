# RPC Endpoints

## Ethereum-compatible RPC endpoints

You can use any [Ethereum library and tool](./) with the IoTeX blockchain by simply pointing them to an IoTeX Gateway node.&#x20;

Below, you find a list of official and third-party IoTeX gateways that [provide an Ethereum-RPC endpoint](https://delegates.iotex.io/get-started/node-configuration/run-the-node#run-as-a-gateway), that you can use to configure any Ethereum wallet or developer tool to interact with the IoTeX blockchain:&#x20;

{% hint style="success" %}
Checkout the "[Run as a Gateway](https://delegates.iotex.io/get-started/node-configuration/run-the-node#run-as-a-gateway)" section of the iotex [full-node documentation](https://delegates.iotex.io) to learn how to run a full node as a network RPC endpoint.
{% endhint %}

### Mainnet \[Chain ID 4689]

<table><thead><tr><th width="362.4995649735719">Endpoint</th><th width="118">Type</th><th width="129">Provider</th><th>More</th></tr></thead><tbody><tr><td>https://babel-api.mainnet.iotex.io</td><td>HTTP</td><td>IoTeX<br>Foundation</td><td><a href="https://iotex.io">iotex.io</a></td></tr><tr><td>wss://babel-api.mainnet.iotex.io/ws</td><td>WSS</td><td>IoTeX<br>Foundation</td><td><a href="https://iotex.io">iotex.io</a></td></tr><tr><td>https://babel-api.mainnet.iotex.one</td><td>HTTP</td><td>IoTeX Foundation</td><td><a href="https://iotex.io">iotex.io</a></td></tr><tr><td>https://babel-api.fastblocks.io</td><td>HTTP</td><td>Fastblocks</td><td><a href="https://fastblocks.io/">fastblock.io</a></td></tr><tr><td>https://iotexrpc.com</td><td>HTTP</td><td>Ankr</td><td><a href="https://iotexrpc.com">iotexrpc.com</a></td></tr><tr><td>https://rpc.ankr.com/iotex</td><td>HTTP</td><td>Ankr</td><td><a href="https://ankr.com">ankr.com</a></td></tr><tr><td>https://4689.rpc.thirdweb.com</td><td>HTTP</td><td>Thirdweb</td><td><a href="https://thirdweb.com/iotex-network">Thirdweb</a></td></tr></tbody></table>

### Testnet \[Chain ID 4690]

<table><thead><tr><th width="362.5471637775761">Endpoint</th><th width="120">Type</th><th width="127">Text</th><th>More</th></tr></thead><tbody><tr><td>https://babel-api.testnet.iotex.io</td><td>HTTP</td><td>IoTeX Foundation</td><td><a href="https://iotex.io">iotex.io</a></td></tr><tr><td>wss://babel-api.testnet.iotex.io/ws</td><td>WSS</td><td>IoTeX Foundation</td><td><a href="https://iotex.io">iotex.io</a></td></tr><tr><td> https://babel-api.testnet.iotex.one</td><td>HTTP</td><td>IoTeX Foundation</td><td><a href="https://iotex.io">iotex.io</a></td></tr><tr><td> https://babel-api.testnet.iotex.one/wss</td><td>WSS</td><td>IoTeX Foundation</td><td><a href="https://iotex.io">iotex.io</a></td></tr></tbody></table>

**Example**

To get the balance of the IoTeX address `ukzv5m6xnsg3gzaec3shew8nw03cch2x53d6v6` you first convert it into the Ethereum address format using ioctl:

```bash
$ ioctl account ethaddr io1ukzv5m6xnsg3gzaec3shew8nw03cch2x53d6v6
io1ukzv5m6xnsg3gzaec3shew8nw03cch2x53d6v6 - 0xE584ca6F469c11140Bb9c4617Cb8f373E38C5D46
```

which gives you the following Ethereum address:`0xE584ca6F469c11140Bb9c4617Cb8f373E38C5D46.`&#x20;

Then you can query the Babel endpoint according to the Ethereum JSON RPC API:&#x20;

```bash
» curl -X POST -H "Content-Type:application/json" --data '{"id": 1, "jsonrpc": "2.0", "method": "eth_getBalance", "params": ["0xE584ca6F469c11140Bb9c4617Cb8f373E38C5D46", ""]}' https://babel-api.mainnet.iotex.io
{
  "id": 1,
  "jsonrpc": "2.0",
  "result": "0x10f0cf064dd59200000"
}
```

Which returns the balance `0x10f0cf064dd59200000` (hex) for the address, [expressed in Rau units](../basic-concepts/iotx-token.md#iotx-fractions) (i.e. 5000000000000000000000 Rau, equivalent to 5000 IOTX).

Check out the official Ethereum JSON-RPC API Documentation at:

{% embed url="https://eth.wiki/json-rpc/API#json-rpc-methods" %}
Official Ethereum JSON-RPC API Documentation
{% endembed %}

## Chain ID

The `chainID` chain identifier was introduced by Ethereum in [`EIP-155`](https://eips.ethereum.org/EIPS/eip-155#list-of-chain-ids) **to prevent replay attacks between Ethereum-compatible chains**, it is a way to tell chains apart, where Ethereum was assigned a `chainID` of 1.&#x20;

In respect of this `EIP`, IoTeX `chainIDs` have been picked as follows:

<table><thead><tr><th width="298">Network</th><th>chainID</th></tr></thead><tbody><tr><td>IoTeX Mainnet</td><td><code>4689</code></td></tr><tr><td>IoTeX Testnet</td><td><code>4690</code></td></tr></tbody></table>

## Supported API calls

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
