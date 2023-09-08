# Truffle

[Truffle](https://www.trufflesuite.com/docs/truffle/overview) is a world class development environment, testing framework and asset pipeline for blockchains using the Ethereum Virtual Machine (EVM), aiming to make life as a developer easier.

This guide describes how to configure Truffle when you want to deploy your smart contracts on the IoTeX Network.

Let's assume that you already created a Truffle project and you want now use the `truffle migrate` command to deploy it on IoTeX.&#x20;

{% hint style="info" %}
We will use `https://babel-api.testnet.iotex.io` for IoTeX Testnet. \
Check out the [RPC Endpoint](rpc-endpoints.md) section for more info.&#x20;
{% endhint %}

## 1. Install the hdwallet-provider package

```
npm install @truffle/hdwallet-provider --save
```

## 2. Configure Truffle

You can configure Truffle accounts by using a mnemonic phrase or private keys.

### 2.1. Using Mnemonic phrase

Modify `truffle-config.js` as below:

```javascript
const { MNEMONIC } = process.env;
const HDWalletProvider = require('@truffle/hdwallet-provider');

module.exports = {
  networks: {
    dev: {
      provider: () =>
        new HDWalletProvider({
          mnemonic: {
            phrase: MNEMONIC,
          },
          providerOrUrl: "https://babel-api.testnet.iotex.io",
          shareNonce: true
        }),
      network_id: 4690,    // IOTEX mainnet chain id 4689, testnet is 4690
      gas: 8500000,
      gasPrice: 1000000000000,
      skipDryRun: true
    }
  }
}
```

and deploy with:

```
MNEMONIC=`Your mnemonic` truffle migrate --reset --network dev
```

### 2.2. Using private keys

Modify `truffle-config.js` as below:

```javascript
const HDWalletProvider = require('@truffle/hdwallet-provider');

const privateKeys = [
  "3f841bf589fdf83a521e55d51afddc34fa65351161eead24f064855fc29c9580",
  "9549f39decea7b7504e15572b2c6a72766df0281cea22bd1a3bc87166b1ca290",
];

module.exports = {
  networks: {
    dev: {
      provider: () => new HDWalletProvider(privateKeys, "https://babel-api.testnet.iotex.io", 0, 2),
      network_id: 4690,    // IOTEX mainnet chain id 4689, testnet is 4690
      gas: 8500000,
      gasPrice: 1000000000000,
      skipDryRun: true
    }
  }
}
```

## Deploy

Finally, deploy your contracts with:

```
truffle migrate --reset --network dev
```
