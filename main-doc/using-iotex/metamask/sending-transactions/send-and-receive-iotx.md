---
description: A comprehensive guide to withdrawing, depositing to exchanges
---

# Send & Receive IOTX

## Introduction

Welcome to our guide on sending and receiving IOTX tokens. This guide is designed to help you understand how to transfer IOTX tokens between exchanges and personal wallets, such as Metamask or ioPay. We'll also cover important considerations for users withdrawing IOTX from exchanges like [Coinbase.com](https://www.coinbase.com/), which only support IOTX tokens on the Ethereum blockchain.

## Sending IOTX Tokens

### Withdrawing from an Exchange to a Personal Wallet

{% hint style="info" %}
Before withdrawing IOTX from the exchange, ensure that

* you have a [compatible wallet](../).
* your wallet is [set on the IoTeX Network](https://app.gitbook.com/o/-MQ9LhchTp7\_QJr-AYG0/s/-MUPHwAAaa4\_zIrX70rA/\~/changes/317/main-doc/using-iotex/getting-started/metamask/\~/page#switching-between-networks).
{% endhint %}

1. Log into your exchange account&#x20;
2. Navigate to the `withdrawal` section.
3. Select `IOTX` as the token to withdraw.
4. Enter the address of your personal wallet.
5. If required, select `IoTeX` as the destination network

{% hint style="info" %}
**Note**

Some exchanges, when withdrawing to the IoTeX network, expect you to input the recipient address in the IoTeX _"native format,"_ which starts with `"io1..."`. In this case, if your recipient address is in the `"0x..."` (Ethereum) format, you must convert it to the IoTeX native format using the IoTeX Address Converter to make the exchange accept it.

[IoTeX Address Converter ->  ](https://developers.iotex.io/dev-tools?tool=address-convert)
{% endhint %}

### Depositing from Personal Wallet to Exchange

1. Log into your exchange account and obtain the deposit address for `IOTX`.
2. Make sure your exchange accepts IOTX deposits on the IoTeX Network for that deposit address.
3. Initiating the Transfer**:**
   * Open your personal wallet (Metamask, ioPay, etc.).
   * Ensure you've [selected the IoTeX Network](../#switching-between-networks)
   * Select your IoTeX wallet and click "Send".
   * Enter the exchange's deposit address as the recipient.
   * Confirm the transaction details and complete the transfer.

## Receiving IOTX Tokens

{% hint style="info" %}
When you need to receive IOTX tokens to your personal wallet, always agree with the sender on what Blockchain Network you expect to receive the tokens, and select the same network in your personal wallet.&#x20;
{% endhint %}

1. Locate and copy your wallet's address.
2. Provide your wallet's address to the sender.
3. Confirm that the sender uses the correct token and blockchain network.

## Special Considerations for Coinbase Users

{% hint style="warning" %}
Some exchanges, like [Coinbase.com](https://coinbase.com), currently supports IOTX only on the Ethereum blockchain. **This means you will receive your IOTX on the Ethereum network when you withdraw from Coinbase.**&#x20;

* Ensure you have enough ETH in your wallet to cover for gas costs on the Ethereum network when you want to transfer your IOTX.
* Check out the IOTX Swap guide below if you want to use your IOTX on the IoTeX blockchain for staking and interacting with IoTeX dApps
{% endhint %}

<details>

<summary>🔄 Swap IOTX on Ethereum with Native IOTX</summary>

[Go to the IOTX swap guide -> ](https://app.gitbook.com/o/-MQ9LhchTp7\_QJr-AYG0/s/-MUPHwAAaa4\_zIrX70rA/\~/changes/317/main-doc/using-iotex/bridging-your-tokens/swapping-iotx-tokens/\~/page)

</details>

## Conclusion

Transferring IOTX tokens can be a seamless process with the right information. Whether you are moving tokens from an exchange to a personal wallet or vice versa, always ensure you are using compatible wallets and networks. For specific needs like staking, the iotube dApp provides a decentralized solution to swap your IOTX tokens on ethereum to the native IoTeX blockchain.
