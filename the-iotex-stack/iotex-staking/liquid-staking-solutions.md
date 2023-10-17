# Liquid Staking Solutions

{% hint style="info" %}
🚧 **Work in Progress!**\
This section is currently under construction. Please check back soon for updates. We appreciate your patience and enthusiasm for IoTeX!

Feel free to explore the rest of the [Staking docs ->](./)
{% endhint %}

## Overview

Staking in the IoTeX blockchain is implemented natively, which prevents direct interaction with smart contracts. While IIP12 addressed the the possibility of accessing the full staking protocol from the Ethereum JSON API with a virtual contract, it is not a real EVM smart contract and thus is not visible and cannot be executed by other smart contracts.

This limitation has been addressed with the adoption of IIP13, that allows representing IoTeX staking buckets as **Non-fungible Tokens** (NFTs). This allows liquid staking solutions that rely on smart contracts to manage their stakes via system-level smart contracts.

In this section we will highlight the details of how Staking as NFT works and provide documentation on how to engage with staking buckets to offer liquid staking solutions on IoTeX.

### How it works

Liquid Staking has been enabled with the implementation of a so called "System Staking Contract". This is the primary contract responsible for providing the functionalities laid out in IIP-13. It manages tasks such as creating, modifying, transferring, and querying staking Buckets and their associated NFT tokens.

[Visit the original IIP-13 Proposal ->](https://github.com/iotexproject/iips/blob/master/iip-13.md)

### The System Staking Contract

[Source Code](https://github.com/iotexproject/iip13-contracts/blob/main/src/SystemStaking.sol) | [ABI](https://github.com/iotexproject/iip13-contracts/blob/main/abi/SystemStaking.abi)

<table><thead><tr><th width="133">Network</th><th width="453">Address</th></tr></thead><tbody><tr><td>Testnet</td><td><code>0x52ab0fe2c3a94644de0888a3ba9ea1443672e61f</code></td></tr><tr><td>Mainnet</td><td><code>0x68db92a6a78a39dcaff1745da9e89e230ef49d3d</code></td></tr></tbody></table>

## Bucket Types

In the context of staking as NFT, a "Bucket Type" represent a specific staking configuration, including the deposit amount, the preset lock duration, and the status of the StakeLock option. Currently, three bucket types are supported in the implementation, that are listed below:

<table><thead><tr><th width="189.33333333333331">Amount (IOTX)</th><th width="154">Duration (Days)</th><th>Duration (Blocks)</th><th>StakeLock</th><th data-hidden>Duration (days)</th><th data-hidden>Duration (blocks)</th><th data-hidden></th></tr></thead><tbody><tr><td>10,000</td><td>91</td><td>1,572,480</td><td>ON</td><td>91</td><td>1,572,480</td><td></td></tr><tr><td>100,000</td><td>91</td><td>1,572,480</td><td>ON</td><td>91</td><td>1,572,480</td><td></td></tr><tr><td>1,000,000</td><td>91</td><td>1,572,480</td><td>ON</td><td>91</td><td>1,572,480</td><td></td></tr></tbody></table>

## Examples

In this section we explore in details how to interact with the SystemStaking contract from another contract to enable liquid staking dApps.

### Staking IOTX from your Contract

...

\-> Link to how to get the eligible delegates in the frontend

\-> Link to how to get the available bucket types in the frontend

### Editing a staking Bucket

...

### Unstaking a bucket

...

### Withdrawing a bucket

...

## Appendix

### Setting up the Environment

### Available bucket types

### Eligible Delegates



## Conclusion

These are the foundational steps for interacting with IIP-13 contracts, that allows the creation of Liquid Staking solutions. Liquid staking allows users to access the benefits of staking in a blockchain network while still maintaining liquidity and flexibility over their staked assets, which create a more attractive and versatile staking experience.

For more advanced operations and deeper insights, refer to the IIP-13 official documentation and the contract's source code.

