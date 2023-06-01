# Chainlink relayer

Chainlink Relayer instantly relays Chainlink price feeds on Ethereum to IoTeX network, for enabling dApps where price feeds are needed

* The prices are relayed to a contract (called shadow aggregator) on IoTeX which has exactly the same interface as Chainlink's aggregator, and it makes dApps to migrate to use Chainlink effortlessly once their integration with IoTeX is done.
* The client waits for 20 blocks (around 5 minutes) to confirm a transaction.
* Anyone can run a relayer to relay the information. So it is permissionless!

### Shadow Aggregators

For each aggregator on Ethereum, we will create a shadow aggregator on IoTeX.

**IoTeX Testnet** The table below lists the shadow aggregators deployed on IoTeX testnet:

<table><thead><tr><th width="142">Pair</th><th width="89">Dec</th><th width="277">Aggregator</th><th width="266">Shadow Aggregator</th></tr></thead><tbody><tr><td>BTC/USD</td><td>8</td><td><a href="https://etherscan.io/address/0xF4030086522a5bEEa4988F8cA5B36dbC97BeE88c">0xF4030086522a5bEEa4988F8cA5B36dbC97BeE88c</a></td><td><a href="https://testnet.iotexscan.io/address/0xc4A29a94f12be03033daa4e6Ce9b9678c26275a2">0xc4A29a94f12be03033daa4e6Ce9b9678c26275a2</a></td></tr><tr><td>ETH/USD</td><td>8</td><td><a href="https://etherscan.io/address/0x5f4eC3Df9cbd43714FE2740f5E3616155c5b8419">0x5f4eC3Df9cbd43714FE2740f5E3616155c5b8419</a></td><td><a href="https://testnet.iotexscan.io/address/0x107DF34D3B2F471eEff880956957e5068A987b81">0x107DF34D3B2F471eEff880956957e5068A987b81</a></td></tr><tr><td>BUSD/USD</td><td>8</td><td><a href="https://etherscan.io/address/0x833D8Eb16D306ed1FbB5D7A2E019e106B960965A">0x833D8Eb16D306ed1FbB5D7A2E019e106B960965A</a></td><td><a href="https://testnet.iotexscan.io/address/0x8A6A4407c77F1e04C39bAd8C089D639cbda40Df5">0x8A6A4407c77F1e04C39bAd8C089D639cbda40Df5</a></td></tr><tr><td>USDC/USD</td><td>8</td><td><a href="https://etherscan.io/address/0x8fFfFfd4AfB6115b954Bd326cbe7B4BA576818f6">0x8fFfFfd4AfB6115b954Bd326cbe7B4BA576818f6</a></td><td><a href="https://testnet.iotexscan.io/address/0xB1aa8c29d96720A80AFe9e3F6CD48822D27C8d54">0xB1aa8c29d96720A80AFe9e3F6CD48822D27C8d54</a></td></tr><tr><td>USDT/USD</td><td>8</td><td><a href="https://etherscan.io/address/0x3E7d1eAB13ad0104d2750B8863b489D65364e32D">0x3E7d1eAB13ad0104d2750B8863b489D65364e32D</a></td><td><a href="https://testnet.iotexscan.io/address/0x63Bd61A642d1f3dbf1f47006AC03CD7e7eb72f63">0x63Bd61A642d1f3dbf1f47006AC03CD7e7eb72f63</a></td></tr><tr><td>DAI/USD</td><td>8</td><td><a href="https://etherscan.io/address/0xAed0c38402a5d19df6E4c03F4E2DceD6e29c1ee9">0xAed0c38402a5d19df6E4c03F4E2DceD6e29c1ee9</a></td><td><a href="https://testnet.iotexscan.io/address/0x9673b1b3fbB96E24f1C1AB40421Db9465f0f1151">0x9673b1b3fbB96E24f1C1AB40421Db9465f0f1151</a></td></tr><tr><td>IOTX/USD</td><td>8</td><td><a href="https://etherscan.io/address/0x96c45535d235148Dc3ABA1E48A6E3cFB3510f4E2">0x96c45535d235148Dc3ABA1E48A6E3cFB3510f4E2</a></td><td><a href="https://testnet.iotexscan.io/address/0xf55dA02f8266eC89A58C6De361cf92ce9cee21fe">0xf55dA02f8266eC89A58C6De361cf92ce9cee21fe</a></td></tr></tbody></table>

**IoTeX Mainnet**

<table><thead><tr><th width="146">Pair</th><th width="76">Dec</th><th width="269">Aggregator</th><th>Shadow Aggregator</th></tr></thead><tbody><tr><td>BTC/USD</td><td>8</td><td><a href="https://etherscan.io/address/0xF4030086522a5bEEa4988F8cA5B36dbC97BeE88c">0xF4030086522a5bEEa4988F8cA5B36dbC97BeE88c</a></td><td><a href="https://iotexscan.io/address/0x631f185E832DfBC3aDfeFa37c83aA23f75d0c8c7">0x631f185E832DfBC3aDfeFa37c83aA23f75d0c8c7</a></td></tr><tr><td>ETH/USD</td><td>8</td><td><a href="https://etherscan.io/address/0x5f4eC3Df9cbd43714FE2740f5E3616155c5b8419">0x5f4eC3Df9cbd43714FE2740f5E3616155c5b8419</a></td><td><a href="https://iotexscan.io/address/0x0a1886890c0633e32746bc5021E3c1EfAD2bd662">0x0a1886890c0633e32746bc5021E3c1EfAD2bd662</a></td></tr><tr><td>BUSD/USD</td><td>8</td><td><a href="https://etherscan.io/address/0x833D8Eb16D306ed1FbB5D7A2E019e106B960965A">0x833D8Eb16D306ed1FbB5D7A2E019e106B960965A</a></td><td><a href="https://iotexscan.io/address/0x071F9106A9957e530a4B48269e38640ebAfc0f34">0x071F9106A9957e530a4B48269e38640ebAfc0f34</a></td></tr><tr><td>USDC/USD</td><td>8</td><td><a href="https://etherscan.io/address/0x8fFfFfd4AfB6115b954Bd326cbe7B4BA576818f6">0x8fFfFfd4AfB6115b954Bd326cbe7B4BA576818f6</a></td><td><a href="https://iotexscan.io/address/0xC296E7e92B3Ce84e9bF5780a47eF231E14A4506d">0xC296E7e92B3Ce84e9bF5780a47eF231E14A4506d</a></td></tr><tr><td>USDT/USD</td><td>8</td><td><a href="https://etherscan.io/address/0x3E7d1eAB13ad0104d2750B8863b489D65364e32D">0x3E7d1eAB13ad0104d2750B8863b489D65364e32D</a></td><td><a href="https://iotexscan.io/address/0xa900b5eB48F5A1122F9bfA660dd0B61Ddc56C872">0xa900b5eB48F5A1122F9bfA660dd0B61Ddc56C872</a></td></tr><tr><td>DAI/USD</td><td>8</td><td><a href="https://etherscan.io/address/0xAed0c38402a5d19df6E4c03F4E2DceD6e29c1ee9">0xAed0c38402a5d19df6E4c03F4E2DceD6e29c1ee9</a></td><td><a href="https://iotexscan.io/address/0x95eBC95FF2b81866D7Bc1c3c1257533795CF96B7">0x95eBC95FF2b81866D7Bc1c3c1257533795CF96B7</a></td></tr><tr><td>IOTX/USD</td><td>8</td><td><a href="https://etherscan.io/address/0x96c45535d235148Dc3ABA1E48A6E3cFB3510f4E2">0x96c45535d235148Dc3ABA1E48A6E3cFB3510f4E2</a></td><td><a href="https://iotexscan.io/address/0x95eBC95FF2b81866D7Bc1c3c1257533795CF96B7">0x0F7AbD6b99d5D6876C812dAc22A2c8A8A6297D90</a></td></tr></tbody></table>

<table><thead><tr><th width="131.66666666666669">Pair</th><th width="86">Dec</th><th>Aggregator</th></tr></thead><tbody><tr><td>IOTX/USD</td><td>8</td><td><a href="https://iotexscan.io/address/0x267Ef702F3422cC55C617218a4fB84446F5Ec646">0x267Ef702F3422cC55C617218a4fB84446F5Ec646</a></td></tr></tbody></table>

### Exchange Aggregators

Exchange aggregator has the same interface as Chainlink aggregator. The prices are read from exchanges, and the medium value of these prices will be feed to exchange aggregator by permitted relayers if

* the value is of a 0.5% deviation from the last price
* or the time interval is more than 1 hour

Exchanges used for fetching IOTX price are binance, huobi, coingeko, kucoin, coinbase.

### Run a Relayer

#### Prepare Config File

1. fill "databaseURL" with your DB link
2. input ethereum rpc url in "sourceClientURL"
3. input your relayer private key, make sure the account has sufficient balance

#### Start Relayer Service

`go run main.go -config config.yaml`
