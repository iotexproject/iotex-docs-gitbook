# $IOTX Token

## Overview <a href="#overview" id="overview"></a>

The IOTX token, commonly known as "_iotex_," serves as the native cryptocurrency of the IoTeX blockchain, playing a role similar to Ether (ETH) in Ethereum. It underpins a marketplace for computational power, ensuring that nodes who run the blockchain are financially motivated to validate and process transactions, as well as to supply the computational power required to execute smart contracts across the network. This mechanism is vital for maintaining the network's operation and efficiency.

[-> Read more about IOTX token in this blog article](https://iotex.io/blog/iot-investments-for-the-future/)

## Tokenomics <a href="#tokenomics" id="tokenomics"></a>

| Info               | Value                       |
| ------------------ | --------------------------- |
| Max Supply         | 10 Billions IOTX            |
| Total Supply       | 9,441,378,959 IOTX          |
| Circulating Supply | All IOTX are in circulation |

[-> Check out IOTX on CoinMarketCap](https://coinmarketcap.com/currencies/iotex/)

[-> Check out IOTX on CoinGecko](https://www.coingecko.com/en/coins/iotex)

## Transaction fees <a href="#transaction-fees" id="transaction-fees"></a>

In the IoTeX network, anyone initiating a transaction must pay a fee in $IOTX, similar to Ethereum's transaction fee structure. These transaction fees, known as "_gas_", along with donations, for example, go into a **Reward Pool** which also includes all Roll DPoS rewards such as block rewards, epoch bonus, and so on.

{% hint style="info" %}
💡 Did you know? \
Currently 12% of the total $IOTX supply has been deposited into the Reward Pool.
{% endhint %}

This Reward Pool is used to compensate the network nodes responsible for validating, executing, and recording the transaction on the blockchain. The size of the fee corresponds to the computational effort required for the transaction, helping to prevent network abuse by discouraging excessively demanding computational tasks without appropriate compensation.

{% hint style="info" %}
Feel free to refer to [this community conversation](https://community.iotex.io/t/hi-where-does-the-revenue-gas-from-the-iotex-protocol-go/11944) in the **IoTeX Community Forum** if you'd like to learn more.&#x20;
{% endhint %}

## IOTX Token utility <a href="#iotx-token-utility" id="iotx-token-utility"></a>

IOTX serves multiple crucial roles in maintaining the crypto-economic security of the IoTeX network:

**Rewards:** IOTX is used to reward nodes who successfully propose new blocks and identify fraudulent activities within the network.

**Staking by Validators:** Validator nodes stake IOTX as a form of commitment and collateral, helping to safeguard the network against dishonest behaviors.

**Delegate Election:** IOTX is crucial for staking by token holders, who use it to vote for delegates. This process is vital for maintaining decentralized governance and overall network security.

**Burn-Drop Mechanism:** In a unique deflationary tactic specific to the IoT environment, IOTX implements the "Burn-Drop" scheme. Whenever a new IoT device is registered on the IoTeX blockchain, a specified number of tokens are burned, and a corresponding amount is airdropped to stakers, simultaneously reducing the total supply and rewarding active participants.

## Instances of the IOTX token <a href="#instances-of-the-iotx-token" id="instances-of-the-iotx-token"></a>

### IOTX ERC20 <a href="#iotx-erc20" id="iotx-erc20"></a>

IOTX ERC20 token is the original form of the IOTX token that was issued on the Ethereum blockchain during the initial development phase of the IoTeX blockchain protocol. Prior to the launch of the IoTeX blockchain in 2019, IOTX was primarily an Etherum ERC20 token to facilitate early distribution and community engagement.

<table><thead><tr><th width="161">Blockchain</th><th width="131">Symbol</th><th>Contract Address</th></tr></thead><tbody><tr><td>Ethereum</td><td><code>IOTX</code></td><td><code>0x6fb3e0a217407efff7ca062d46c26e5d60a14d69</code></td></tr></tbody></table>

<details>

<summary>Read more: <strong>History of the ERC20 IOTX token</strong></summary>

**Migration to Native IOTX**

With the official bootstrap of the IoTeX blockchain in 2019, the native IOTX token became available. Token holders of the ERC20 IOTX were encouraged to swap their tokens for the native IOTX to take full advantage of the newly launched blockchain’s features. The swap was facilitated through a service originally known as "_tube_," designed specifically for this transition.

**Swap Mechanism**

The swap from ERC20 IOTX to native IOTX was also supported by major centralized exchanges, including Binance and Gate.io, ensuring a broad and accessible platform for all token holders to migrate their assets seamlessly. While it was initially planned to phase out the "tube" service post-migration, considerations regarding user access and token utility led to the service remaining operational.

**Evolution into ioTube**

Over time, the tube service evolved into what is now known as the [**ioTube bridge**](https://iotube.org). This evolution expanded the functionality from a simple one-way IOTX swap service to two-was swap, and then to a more comprehensive bridge service between various blockchains supporting any token.

**Current Swap Process**

Today, holders of the ERC20 IOTX can still swap their tokens to native IOTX using the following multi-step process through [iotube](https://iotube.org):

1. **Swap on Ethereum**: Users first swap their ERC20 IOTX for CIOTX (CrossChain IOTX) on Ethereum using [Uniswap](https://uniswap.org). This step is necessary to convert the token into a format compatible with the iotube bridge.
2. **Bridge to IoTeX**: The CIOTX tokens are then sent through the iotube bridge to the IoTeX blockchain. Upon reaching IoTeX, CIOTX is converted into WIOTX (Wrapped IOTX), an ERC20-wrapped version of the native token on the IoTeX blockchain.
3. **Unwrap to Native IOTX**: Finally, users can unwrap their WIOTX to receive native IOTX tokens, completing the migration process using the [wrapping service provided by iotube](https://iotube.org/wrap).

</details>

### Wrapped IOTX (WIOTX)

`WIOTX` is an ERC20 token deployed on the IoTeX blockchain. Due to its exchangeability and representation on the IoTeX blockchain, WIOTX is commonly referred to as "Wrapped IOTX." It represents an ERC20-wrapped version of the native IOTX token, enabling it to interact with other ERC20 compatible services within the IoTeX ecosystem. This token typically originates from the bridging of `CIOTX` tokens from the Ethereum blockchain to the IoTeX blockchain. This process is facilitated through [iotube.org](https://iotube.org/), a cross-chain bridge.

`WIOTX` is designed to be directly exchangeable with the native IOTX token at a consistent 1:1 ratio. This exchange (also called "unwrapping") can be performed on the [dedicated iotube service](https://bridge.iotex.io/wrap) or alternatively, on the  [mimo Decentralized Exchange (DEX)](https://mimo.finance).&#x20;

<table><thead><tr><th width="174">Blockchain</th><th width="121">Symbol</th><th>Contract Address</th></tr></thead><tbody><tr><td>IoTeX</td><td><code>WIOTX</code></td><td><code>0xa00744882684c3e4747faefd68d283ea44099d03</code></td></tr></tbody></table>

### **CrossChain IOTX (CIOTX)**

CIOTX, also known as "CrossChain IOTX," is an ERC20 token utilized within the [iotube](http://iotube.org) bridge ecosystem. It is designed to facilitate the bridging of the native IOTX token between the IoTeX blockchain and all other blockchains supported by iotube. This interoperability enables seamless IOTX token transfers across different blockchain networks. CIOTX maintains a consistent 1:1 swap ratio with both the native IOTX token and the Wrapped IOTX (WIOTX) token on the IoTeX blockchain, utilizing the  [dedicated service provided by iotube](https://bridge.iotex.io/wrap).&#x20;

<table><thead><tr><th width="175">Blockchain</th><th width="120">Symbol</th><th>Contract Address</th></tr></thead><tbody><tr><td>IoTeX</td><td><code>CIOTX</code></td><td><code>0x99B2B0eFb56E62E36960c20cD5ca8eC6ABD5557A</code></td></tr><tr><td>Polygon</td><td><code>CIOTX</code></td><td><code>0x300211Def2a644b036A9bdd3e58159bb2074d388</code></td></tr><tr><td>BSC</td><td><code>CIOTX</code></td><td><code>0x2aaF50869739e317AB80A57Bf87cAA35F5b60598</code></td></tr><tr><td>Ethereum</td><td><code>CIOTX</code></td><td><code>0x9F90B457Dea25eF802E38D470ddA7343691D8FE1</code></td></tr></tbody></table>

## IOTX Fractions <a href="#iotx-fractions" id="iotx-fractions"></a>

6 fractions of the IOTX token are defined, where `1 Rau` is the smallest `IOTX` token unit:

| Fraction | IOTX Value | Rau Value |
| -------- | ---------- | --------- |
| 1 Rau    | 10⁻¹⁸ IOTX | 1 Rau     |
| 1 Krau   | 10⁻¹⁵ IOTX | 10³ Rau   |
| 1 Mrau   | 10⁻¹² IOTX | 10⁶ Rau   |
| 1 Grau   | 10⁻⁹ IOTX  | 10⁹ Rau   |
| 1 Qev    | 10⁻⁶ IOTX  | 10¹² Rau  |
| 1 Jing   | 10⁻³ IOTX  | 10¹⁵ Rau  |
| 1 IOTX   | 1 IOTX     | 10¹⁸ Rau  |
