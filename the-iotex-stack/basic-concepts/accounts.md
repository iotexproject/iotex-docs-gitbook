# Wallet Accounts

## Introduction

An **Account** uniquely identifies any entity actively participating in the IoTeX network: A user, a device, an enterprise, or even software on the blockchain itself (a so-called _smart contract_). Each IoTeX account has a **private key** and a corresponding **public key** associated with it.&#x20;

## Account Address

As with other blockchain networks, following a specific set of transformations, the public key is usually transformed into a human-readable string, which is referred to as the **address** of the account,&#x20;

IoTeX specifies an address format made of 41 characters, starting by `io1...` such that a typical address in the IoTeX blockchain looks like the one below:

`io1z3lgqhy93pqqnyvsugyd0gz2wne2p2kglr5cdd`

which was obtained from the following public key:

`0700898c9dcae0279c88318003ee210e1ee2514121d292d2f03739498ce95f4e`

Nonetheless, if you convert that public key using the Ethereum address format specification, you will get the following Ethereum address representation:

`0x147e805c858840099190e208d7A04A74F2A0AAC8`

Both the IoTeX address and the Ethereum address representations above **refer to the same blockchain account** because they represent the same public key. Check out the section [Address Conversion](address-conversion.md) to learn more about IoTeX and Ethereum address representations.

## Address types

IoTeX is an Ethereum-compatible smart contract platform, so in the same way as Ethereum two types of accounts are defined:&#x20;

**Externally** **owned** **accounts**: have a known **private key** associated with them (typically owned by people, enterprises, or IoT devices) and can **initiate** actions such as token transfers or contract calls

**Smart contract** **accounts:** have no known private key associated, hence they cannot initiate actions, but they have "code" associated with them. The code of a smart-contract account is run each time a "contract call" action is sent to the smart-contract address by either an externally owned account or another smart contract.

{% hint style="info" %}
Learn more about smart-contract accounts in the official Ethereum documentation:
{% endhint %}

{% embed url="https://ethdocs.org/en/latest/contracts-and-transactions/account-types-gas-and-transactions.html#contract-accounts" %}
