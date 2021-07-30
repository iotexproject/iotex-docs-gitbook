---
description: Web3 Development and Solidity support
---

# Ethereum Development

![](../.gitbook/assets/image%20%2859%29.png)

### EVM support

IoTeX is a 100% EVM-compatible smart-contract platform. IoTeX can run any existing **Solidity** smart contract with no change to the code. IoTeX implements the EVM "**Istanbul"** release, which brings the following improvements over the previous version:

* Align the costs of opcodes with their computational costs and improve denial-of-service attack resilience
* Make layer 2 solutions based on SNARKs and STARKs more performant.
* Enable interoperation with Zcash
* Allow contracts to introduce more creative functions.

### Web3 Tools support

Besides its native transactions, IoTeX also natively supports Ethereum transactions. Thanks to the [Babel service](../reference/babel-web3-api.md) \(an Ethereum API Gateway for the IoTeX blockchain\) users and developers can now take advantage of the rich ecosystem of existing Ethereum tools to interact and build on IoTeX: tools like [MetaMask](../get-started/iotex-wallets/metamask.md), [Truffle](truffle.md), or [The Graph ](subgraph.md)can work natively with IoTeX by just pointing them to a **Babel Endpoint**!

In the following section, we will see how to configure the most popular Ethereum tools to be used on IoTeX. For more information, check out the Babel Service API documentation:

{% page-ref page="../reference/babel-web3-api.md" %}

