# Hardhat

**Hardhat** is a development environment to compile, deploy, test, and debug your Ethereum software. This guide describes how to **configure Hardhat to deploy contracts on the IoTeX blockchain**.

If you want to learn more about Hardhat and how to use it, please refer to the official documentation:

{% embed url="https://hardhat.org/getting-started/" %}

We assume you have already created a project in Hardhat.

### Configure Hardhat

You can configure hardhat deployment accounts using a mnemonic phrase, or by setting an array of private keys, which can be also input from the command line or set in the `.env` configuration file. As this is not the scope of this documentation, we refer you to the [hardhat network configuration docs](https://hardhat.org/config/#hardhat-network).&#x20;

#### 1.2 Use Private Key

To have hardhat deploy to IoTeX, simply modify `hardhat-config.js` as below,

```
module.exports = {
  networks: {
    dev: {
      url: "https://babel-api.testnet.iotex.io,
      accounts: ['your private key'],
      chainId: 4690,
      gas: 8500000,
      gasPrice: 1000000000000
    },
  },
  ...
};
```

next, you can deploy as usual:

```
npx hardhat run scripts/sample-script.js --network dev
```
