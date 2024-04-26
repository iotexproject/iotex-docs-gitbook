# Deploy a token with Hardhat

In this section we'll show how to deploy a simple ERC20 token for your DePIN project using Hardhat and [OpenZeppelin](https://www.openzeppelin.com/) (a library of community contributed smart contracts). &#x20;

As mentioned in the [Web3 Development section](../../web3-development/), the [**IoTeX**](https://iotex.io/) Blockchain implements a full-featured **Ethereum Virtual Machine (EVM)**, allowing you to use all your favorite Ethereum tools.  The currently supported EVM version in **Shanghai**, which allows you to build using the Solidity compiler version **v0.8.20**.&#x20;

### Environment setup and writing your contract&#x20;

Given that you can use your favorite Ethereum tools, all you have to do to deploy your own ERC20 token on the IoTeX Testnet or Mainnet, is to follow this [detailed Hardhat guide on how to deploy your first token](https://hardhat.org/tutorial). The guide will walk you through the steps necessary to set up your own environment, write your token contract and finally deploy it.&#x20;

As mentioned earlier you could also use the OpenZeppelin Library in your project, or the OpenZeppelin Wizard tool. More info can be found on the OpenZeppelin official site, [here](https://www.openzeppelin.com/contracts).&#x20;

### Deploying on the IoTeX Testnet

{% hint style="info" %}
**NOTE**: In order to deploy on the **IoTeX Testnet**, all you have to do is to update the `hardhat.config.js` file from the guide above with the IoTeX Testnet configuration, which looks like below 👇
{% endhint %}

```
require("@nomicfoundation/hardhat-toolbox");

const IOTEX_PRIVATE_KEY = "<YOUR PRIVATE KEY HERE>";

module.exports = {
  solidity: "0.8.20",
  networks: {
    testnet: {
      // These are the official IoTeX endpoints to be used by Ethereum clients
      // Testnet https://babel-api.testnet.iotex.io
      // Mainnet https://babel-api.mainnet.iotex.io
      url: `https://babel-api.testnet.iotex.io`,

      // Input your Metamask testnet account private key here
      accounts: [`${IOTEX_PRIVATE_KEY}`],
    },
  },
};
```

Once updated, you can follow this section on [how to deploy your token to a live network](https://hardhat.org/tutorial/deploying-to-a-live-network).&#x20;

{% hint style="info" %}
**Remember**: In order to deploy to the IoTeX Testnet, you'll need some Test $IOTX. Follow the link below in order to do so👇
{% endhint %}

{% content-ref url="../../iotx-faucets/testnet-tokens.md" %}
[testnet-tokens.md](../../iotx-faucets/testnet-tokens.md)
{% endcontent-ref %}

🎉 Congrats! You've deployed your first token on IoTeX!&#x20;

### Importing the IoTeX Testnet/Mainnet in your Ethereum wallet

In order to import the IoTeX Testnet and Mainnet to your Ethereum Wallet (like MetaMask), login to the IoTeX Developers Portal using your Github account, access the [Developer Tools page](https://developers.iotex.io/dev-tools?tool=network-config), and simply connect your browser wallet.&#x20;
