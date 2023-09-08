---
description: Web3 Development and Solidity support
---

# Web3 Development

![](<../../.gitbook/assets/image (48) (1) (1).png>)

### EVM compatibility

The IoTeX Blockchain implements a full-featured **Ethereum Virtual Machine (EVM)**, allowing you to use **Solidity** as a programming language to create smart contracts on IoTeX or port any existing Ethereum smart contract to IoTeX without changes to the source code.

EVM versions keep evolving over time: the currently supported EVM version in **London**, which allows you to build Dapps using the latest Solidity compiler version v**0.8.14**.&#x20;



Check out our tutorial to get started with smart contract deployment on IoTeX:

{% content-ref url="../launch-dapp/deploy-using-remix.md" %}
[deploy-using-remix.md](../launch-dapp/deploy-using-remix.md)
{% endcontent-ref %}

### Ethereum API compatibility

Besides its native transactions, IoTeX also natively supports Ethereum transactions. Starting from the IoTeX blockchain release 1.7.0, every IoTeX node configured as an API gateway will expose the Ethereum JSON API side by side with the native IoTeX GRPc API. IoTeX Users and developers can now take advantage of the rich ecosystem of existing Ethereum tools, apps, and libraries to interact and build on IoTeX blockchain. Tools like [MetaMask](../wallets/metamask.md), [Truffle](truffle.md), or [Web3.js](https://web3js.readthedocs.io/en/v1.7.1/) can interact directly with IoTeX by just pointing them to an IoTeX node!

In the following section, we will see how to configure the most popular Ethereum tools to use them on the IoTeX blockchain.&#x20;
