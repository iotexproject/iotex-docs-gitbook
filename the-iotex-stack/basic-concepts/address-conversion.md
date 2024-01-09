---
description: >-
  Understand IoTeX Native and Ethereum address representations, and easily
  convert between the two.
---

# Address Conversion

## IoTeX Address format

While IoTeX is fully compatible with Ethereum, you should always remember that IoTeX and Ethereum are **two distinct networks**: you must pay a little attention to some small differences when using Web3 tools with IoTeX. One difference is in the wallet address representation: even though IoTeX and Ethereum use the same cryptography for transaction signatures, IoTeX defines its own [wallet address representation format](accounts-cryptography.md), which is different from the Ethereum representation.

Let's look at an example, consider the following **private key**:\
\
`7fda34c8319534253619f69604ffbd43e315e319b84c03ea4f19e1a0e439a4b1`

given that private key, using elliptic curve cryptography we can derive the corresponding **public key**:\
\
`04ba460edf45c8855cccdec55583972dc9aaaee24513db5b4a1dc110b4a7af095a055a38ae679d178ec8cb3ed855aa2d6d23791b1c51eefc19a6da6ae4191cca80`

Now, since **blockchain addresses** are fundamentally just a "compact" representation of the public key, derived from it by applying a few transformations, the public key above becomes the following "_0x..."_ **address in Ethereum**:

`0x95E20FD5FDd9A8D9D174C7fAE7c3F9eC51BBbF36`

and the following "_io1..."_ **address in IoTeX:**

`io1jh3ql40amx5dn5t5claw0slea3gmh0ek8flwlp`

Both these addresses are nothing more than a different way of representing the same public key, and ultimately **they belong to the same private key**.

Depending on which tool you are using for interacting with the IoTeX blockchain, you may have to convert between the IoTeX representation and the Ethereum representation of the same account: Ethereum tools like Metamask or Truffle and libraries like Web3js as well as Solidity compilers expect addresses written the "_0x.._." Ethereum format. On the other hand, IoTeX tools like the ioPay wallet or the iotex-antenna native SDK expect addresses written in the "_io1..."_ IoTeX format or they may accept both formats for the address.

{% hint style="danger" %}
**Please notice:** You should not get confused between the actual _wallet account_ and its _address representation_: while you can represent a wallet public **address** in different ways, a wallet **account** is uniquely identified with its **private key** and the actual **blockchain network** you are interacting with your wallet or tool.

So, as it's for any other Ethereum compatible chain, if your wallet is configured to interact with the IoTeX blockchain (i.e., the RPC endpoint is set to IoTeX), it doesn't matter the address representation you use: you will always be sending tokens from an IoTeX blockchain account to another IoTeX Blockchain account.
{% endhint %}

## Address conversion and tools

Whenever it's required, you can convert between the two address representations at any time: you have many options to do that, let's see some:

### Command-line

On macOs and Linux, you can install the IoTeX official command-line client `ioctl` and use the `ioctl account ethaddr` command to [convert any address ](https://docs.iotex.io/reference/ioctl-cli-reference/accounts#iotex-eth-address-conversion)between Ethereum and IoTeX representations.

### Web tools

You can use the official IoTeX web tools page to convert your address: just input your address in whatever format, and you will get the other representation:

{% embed url="https://developers.iotex.io/utils/address-convert" %}

Other similar tools have been developed by the community that provide the same functionality, like the following one:

{% embed url="https://iotexlab.io/eth2io" %}
Community Address Conversion Tool
{% endembed %}

### NodeJS package

If you are a javascript developer, you can easily integrate the address conversion functionality into your application by installing the following nodejs package:

```bash
# If using npm package manager
$ npm i @iotexproject/iotex-address-ts
# If using yarn package manager
$ yarn add @iotexproject/iotex-address-ts
```

then import it in your code with:

```javascript
import { from } from "@iotexproject/iotex-address-ts";

const addr = from("0xb8744ae4032be5e5ef9fab94ee9c3bf38d5d2ae0");
console.log(addr.string());
// io1hp6y4eqr90j7tmul4w2wa8pm7wx462hq0mg4tw
console.log(addr.stringEth());
// 0xb8744ae4032be5e5ef9fab94ee9c3bf38d5d2ae0

const addr2 = from("io1hp6y4eqr90j7tmul4w2wa8pm7wx462hq0mg4tw");
console.log(addr2.string());
// io1hp6y4eqr90j7tmul4w2wa8pm7wx462hq0mg4tw
console.log(addr2.stringEth());
// 0xb8744ae4032be5e5ef9fab94ee9c3bf38d5d2ae0
```

check out the GitHub repository here:

{% embed url="https://github.com/iotexproject/iotex-address-ts" %}
