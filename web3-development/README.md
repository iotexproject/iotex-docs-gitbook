---
description: Web3 Development and Solidity support
---

# Web3 Development

![](<../.gitbook/assets/image (48) (1).png>)

### EVM compatibility

IoTeX is a 100% EVM-compatible smart-contract platform. IoTeX can run any existing **Solidity** smart contract with no change to the code. "**Istanbul"** is the currently supported release.

Check out our tutorial to get started with smart contract deployment on IoTeX:

{% content-ref url="../smart-contracts/introduction/deploy-using-remix.md" %}
[deploy-using-remix.md](../smart-contracts/introduction/deploy-using-remix.md)
{% endcontent-ref %}

### Ethereum API compatibility

Besides its native transactions, IoTeX also natively supports Ethereum transactions. Starting from the IoTeX blockchain release 1.7.0, every IoTeX node configured as an API gateway will expose the Ethereum JSON API side by side with the native IoTeX GRPc API. IoTeX Users and developers can now take advantage of the rich ecosystem of existing Ethereum tools, apps, and libraries to interact and build on IoTeX blockchain. Tools like [MetaMask](../get-started/iotex-wallets/metamask.md), [Truffle](truffle.md), or [Web3.js](https://web3js.readthedocs.io/en/v1.7.1/) can interact directly with IoTeX by just pointing them to an IoTeX node!

In the following section, we will see how to configure the most popular Ethereum tools to use them on the IoTeX blockchain. For more information, and the list of public Ethereum API endpoins in the IoTeX network check out:

{% content-ref url="../reference/babel-web3-api.md" %}
[babel-web3-api.md](../reference/babel-web3-api.md)
{% endcontent-ref %}
