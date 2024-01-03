---
description: This page will provide a general overview of IoTeX and its ecosystem.
---

# 🏁 Intro to IoTeX

## Overview

Inspired by Ethereum, IoTeX makes it easy for developers to create trustworthy and decentralized networks, known as <mark style="color:purple;">Decentralized Physical Infrastructure Networks (DePIN)</mark>.&#x20;

Although IoTeX shares many concepts with platforms like Ethereum, it pioneers innovative solutions to address challenges related to transaction speed, cost, and scalability paramount in Decentralized Physical Infrastructure Networks. IoTeX introduces a novel off-chain infrastructure called **W3bstream**, specifically designed to scale data processing and proof generation within DePIN projects using a dedicated Virtual Machine and Zero Knowledge techniques.&#x20;

{% hint style="info" %}
**Don't know what blockchain is?**

If you're unfamiliar with the foundational concepts of **blockchain** and Ethereum, we recommend starting with the official [Intro to Ethereum](https://ethereum.org/en/developers/docs/intro-to-ethereum/).

**Unfamiliar with DePIN?**

For those new to the transformative world of **DePIN applications**, explore these in-depth DePIN overview articles on our blog to get started:

📝 [What are Decentralized Physical Infrastructure Networks (DePIN)?](https://iotex.io/blog/what-are-decentralized-physical-infrastructure-networks-depin/)

📝 [Guest Post: On Decentralized Physical Infrastructure Networks](https://iotex.io/blog/on-decentralized-physical-infrastructure-networks/)
{% endhint %}

## The Blockchain Layer

The IoTeX blockchain is a robust platform known built from scratch with real-world applications in mind. The IoTeX RPC API is compatible with Ethereum and it also integrates the Ethereum Virtual Machine (EVM).&#x20;

IoTeX allows a transaction confirmation speed of 5 seconds and a single-block finality, ensuring quick and reliable token transfer processing and smart contract executions. It supports advanced staking capabilities, including an innovative staking mechanism which allows staking deposits to be represented as NFTs to be utilized in Liquid Staking DeFi applications or traded within the ecosystem.&#x20;

### Quick facts about the IoTeX blockchain

<table><thead><tr><th width="277">Feature</th><th></th><th data-hidden>Value</th><th data-hidden></th></tr></thead><tbody><tr><td><strong>Block Time</strong></td><td>5-second block time</td><td>5-second Block Time</td><td></td></tr><tr><td><strong>Action Confirmation</strong></td><td>7.5 seconds on average, 10 seconds maximum</td><td>Minimum 5 secondss, maximum 10seconds</td><td></td></tr><tr><td><strong>Action Finality</strong></td><td>1-block finality for any blockchain action</td><td>1-Block Finality for all blockchain actions</td><td></td></tr><tr><td><strong>Transaction Validation</strong></td><td>Randomized Delegated Proof of Stake (Roll-DPoS)</td><td>Randomized Delegated Proof of Stake (Roll-DPoS)</td><td></td></tr><tr><td><strong>Consensus Algorithm</strong></td><td>Practical Bizantine Fault Tolerance (PBTF)</td><td>Practical Byzantine Fault Tolerant (PBFT)</td><td></td></tr><tr><td><strong>Ethereum Chain IDs</strong></td><td>4689 (IoTeX Mainnet), 4690 (IoTeX Testnet)</td><td>4689 (Mainnet), 4690 (Testnet)</td><td></td></tr><tr><td><strong>IOTX Total Supply</strong></td><td>9,444,302,397 (all tokens are in circulation)</td><td>9,444,302,397 (all circulating)</td><td></td></tr></tbody></table>

### Consensus Mechanism

At the blockchain layer, IoTeX employs an in-house mechanism called "Randomized Delegated Proof of Stake" (RollDPoS). This improves upon the original DPoS mechanism by adding more decentralization and an additional randomization layer to the block producer selection, thereby increasing security. Consensus is reached through Practical Byzantine Fault Tolerance (PBFT).

{% hint style="info" %}
See the original IoTeX Whitepaper (§6.2) for more details on the IoTeX Consensus Mechanism. [Read the Whitepaper ->](https://github.com/iotexproject/files/blob/main/publications/IoTeX\_Whitepaper\_1.5\_EN.pdf)

To explore our extensive contributions and participation in blockchain and IoT research, visit our[ Research and Contributions Page ->](https://iotex.io/research)
{% endhint %}

### Delegates and Block Producers

Anyone wishing to participate in block generation in the IoTeX network must stake IOTX—the native currency of the IoTeX protocol—and run the [iotex-core](https://github.com/iotexproject) software in the "Delegate" configuration. Among these participants, known as "IoTeX Delegates," Block Producers are elected by the community through "delegating" their IOTX tokens using IoTeX's unique [staking feature](https://stake.iotex.io) and "voting" for a delegate.

The top 36 delegates ranked by votes become "Block Producers" and have the authority to propose and validate new blocks in the network. A structure of rewards and penalties exists to strongly incentivize delegates to operate honestly and maintain high availability online.

{% hint style="info" %}
For those interested in running a Delegate within the IoTeX ecosystem, please refer to the dedicated documentation for comprehensive guidelines and insights. [Read the IoTeX Delegates Documentation ->](https://delegates.iotex.io)
{% endhint %}

### The IOTX Token

**IOTX**, often referred to as "_iotex_", is the native cryptocurrency of the IoTeX network. Much like Ethereum's Ether (ETH), IOTX plays a pivotal role in establishing a marketplace for computational processes. This concept ensures that blockchain nodes are economically incentivized to validate and execute action requests, and to provide computational resources to execute smart contracts in the network.

Any participant initiating an action request, similar to Ethereum's transaction request, must provide a certain amount of IOTX as a "fee" to incentivize the network. This designated amount is rewarded to the blockchain nodes that oversee the validation, execution, and integration of the action into the blockchain.

The amount of IOTX offered reflects the computational resources required for the task. Such a system prevents malicious participants from clogging the network with excessive computational demands, as they are bound to provide corresponding compensation.

IOTX, serves to maintain the network's crypto-economic security through several key functions:

1. It operates as a reward mechanism, compensating those who propose new blocks or identify misleading actions by others.
2. IOTX is staked by validator nodes to reinforce their commitment to the network and acting as collateral against deceitful behaviours.
3. IOTX is also used by token holders to stake. In IoTeX this is pivotal for electing delegates in a decentralized fashion and maintain network security.
4. IOTX is also used in a unique IoT deflationary token economy called _"Burn-Drop"_. Each time a new supported device registers its identity on the IoTeX blockchain, a certain amount of tokens is burned, and another amount is "airdropped" to stakers.

### Smart Contracts

Thanks to the native integration of the EVM, smart contracts on IoTeX function similarly to Ethereum. Developers upload reusable code pieces to the EVM's state, indeed known as "smart contracts." These contracts, once invoked by sending an action to their address with specific parameters, execute the contract specific code performing some computations given certain conditions are met.&#x20;

For instance, transferring IOTX to a designated contract address might result in the assignment of a certain digital asset to the sender. These smart contracts pave the way for developers to create applications ranging from games to financial tools on the IoTeX network.&#x20;

### Wallets

A blockchain wallet application serves as a tool to securely encrypt and store private keys, sign actions, and broadcast them to the blockchain.&#x20;

#### ioPay Mobile

Built by the official IoTeX team, ioPay Mobile serves as the definitive native wallet, facilitating token transfers, contract executions, and staking actions directly from your smartphone.\
[Visit the ioPay Mobile website ->](https://iopay.me)

#### Ethereum Wallets

Desktop wallets, such as Metamask, along with various Ethereum wallets—including hardware wallets—can also be utilized with IoTeX. In the dedicated sections that follow, you will find guidance on configuring both native IoTeX wallets and Web3 wallets.\
[Visit the Wallet Configuration Section ->](https://app.gitbook.com/o/-MQ9LhchTp7\_QJr-AYG0/s/f2s3zCHPO4kfjqwDZ9Gw/)

## W3bstream: Verifiable Computation for DePIN

\[ Quick intro ]

\[ Capabilities walkthrough ]

\[ Use Cases ]

\[ Link to the portal ]

***

## Further Readings

* The IoTeX original Whitepaper from 2018
* The Burn-Drop deflationary IOTX token economy
* Staking on IoTeX
* Running a Delegate
* The W3bstream Portal
