# IoTeX Staking Guide

{% hint style="info" %}
This guide is currently under development to ensure its accuracy and thoroughness. Please check back soon for the finalized version. In the meantime, if you have specific questions please ask in our communities or reach out to the IoTeX team by email.

[Join the Telegram Community ->](https://t.me/iotexgroup)

[Join the Discord Community ->](https://iotex.io/devdiscord)

[Contact IoTeX at support@iotex.io ->](mailto:support@iotex.io)
{% endhint %}

## Why Should You Care About Staking? <a href="#why-should-you-care-about-staking" id="why-should-you-care-about-staking"></a>

A core part of decentralized governance in the IoTeX Network is staking, where token holders deposit (“stake”) IOTX to facilitate network operations, consensus, and governance. By staking, token holders enhance the security of the IoTeX Network and earn IOTX rewards in return. IoTeX utilizes [Roll-DPoS consensus](https://github.com/iotexproject/files/blob/main/publications/Academic\_Paper\_Yellow\_Paper.pdf) (Randomized Delegated Proof-of-Stake), where community-voted Delegates manage consensus on behalf of the IoTeX Network. Anyone can stake their IOTX and vote for one or more Delegates.

[View the Roll-DPoS Consensus <mark style="color:yellow;">Yellow Paper</mark> ->](https://github.com/iotexproject/files/blob/main/publications/Academic\_Paper\_Yellow\_Paper.pdf)

## The IoTeX Staking Portal <a href="#what-e2-80-99s-new-with-the-iotex-staking-portal" id="what-e2-80-99s-new-with-the-iotex-staking-portal"></a>

The Staking Portal is now smoother to use with enhanced performance capabilities. When staking on IoTeX, we want to make it a seamless process for even non-native crypto users to participate!

ioPay 2.0 offers in-app staking for mobile users as well. The [ioPay User Guide](https://iotex.io/blog/iopay-crypto-wallet-tutorial/) will show you exactly how to do so.

This guide will help you navigate the actions and choices available to you when you stake and unstake your IOTX. Thanks for being a vital part of the IoTeX community by being a staker.

Before we get rolling, **check out** [**the latest IoTeX Staking Portal**](https://stake.iotex.io/?ref=iotex.io) **here**. Specific information on the Delegates and the percentages they pay for staking can vary. This is where you’ll get that up-to-date information. Onwards!

## &#x20;<a href="#where-to-buy-iotx" id="where-to-buy-iotx"></a>

Coinbase currently only offers the ERC20 version of IOTX.

**Note:** Only native IOTX can be used for staking in the ioPay app. IoTeX has built a two-way bridge to Ethereum called ioTube, which allows you to swap IOTX-E (ERC20 on Ethereum) to Native IOTX (on IoTeX) and vice versa anytime you want. You can find the swap instructions via ioTube [here](https://community.iotex.io/t/iotube-tutorial-cross-transfer-tokens-between-ethereum-and-iotex/1452?ref=iotex.io).

## How staking works on IoTeX <a href="#how-staking-works-on-iotex" id="how-staking-works-on-iotex"></a>

Staking helps the IoTeX blockchain validate transactions more efficiently and securely. It also guarantees trust, as you are essentially acting as an investor/miner in the blockchain by ensuring the validity of new transactions being added. While your tokens are being utilized by the network, you will be rewarded a percentage of interest back over time plus certain voting powers.

The IoTeX blockchain specifically uses Roll-DPoS consensus, a variant of Delegated Proof of Stake (DPoS). IoTeX designed this mechanism to support the high scalability required for IoT use cases. Roll-DPoS inherits all the advantages of the original DPoS consensus framework and further improves its capabilities. Unlike traditional DPoS that utilizes a fixed number of Delegates, Roll-DPoS randomly selects 24 of the top 36 community-voted Delegates to mine every hour, which greatly improves the decentralization and security of the IoTeX Network without sacrificing performance.

Read our [Roll-DPos Consensus Yellow Paper](https://res.cloudinary.com/dokc3pa1x/image/upload/v1559623484/Research%20Paper/Academic\_Paper\_Yellow\_Paper.pdf?ref=iotex.io) or [watch this video](https://youtu.be/UxNioCBJzoE?ref=iotex.io) to learn more.

To participate in the voting process, IoTeX token-holders stake IOTX tokens and receive one vote for every IOTX staked (1 IOTX = 1 vote). Those who show long-term commitment by setting a predefined stake duration will be rewarded with “bonus votes” that increase the staking rewards received. In addition to stake duration, there are several parameters a voter will choose when creating a new vote.

## How do I stake my IOTX? <a href="#how-do-i-stake-my-iotx" id="how-do-i-stake-my-iotx"></a>

When you begin [staking your IOTX](https://stake.iotex.io/?ref=iotex.io), you will decide on several factors:

### Selecting a Delegate <a href="#delegate" id="delegate"></a>

There are 70+ Delegates that each contribute differently to IoTeX and pay different amounts of rewards to voters. You can switch your vote to another Delegate at any time.

Look at the [Delegates List](https://stake.iotex.io/?ref=iotex.io) to learn about what each delegate offers. When considering your choice of delegate, you may want to weigh both the percentage rewards they offer as well as what they state they will do with their rewards.

#### **What is a Hermes delegate?**

Hermes is an IoTeX tool designed to bring reliability and transparency to the rewards distribution process for both Delegates and voters. With Hermes, Delegates can auto-distribute rewards every day, while their voters can easily track their reward payments. Delegates that currently use Hermes have a ‘Hermes’ badge (winged icon) on the staking page.

See the full information about Delegates and their rewards/performances using IoTeX’s [SmartStake](https://iotex.smartstake.io/?ref=iotex.io) tool.

**Note:** in order to receive staking rewards from Binance Staking delegate, you’ll need to stake directly via: [https://www.binance.com/en/pos](https://www.binance.com/en/pos?ref=iotex.io)**.** You will not receive staking rewards if you stake directly via ioPay.

### Decide the Amount <a href="#amount" id="amount"></a>

This determines the number of IOTX you wish to stake/vote. You can add IOTX to an existing bucket after your initial vote (must have the stake lock ON).

### Set the Staking Duration <a href="#staking-duration" id="staking-duration"></a>

This is the amount of time you wish to lock your tokens (between 0-1050 days). The longer you lock your deposit, the more bonus votes (and therefore rewards) you get. Your stake duration essentially serves as a countdown timer until you can unstake your IOTX. When the remaining lock time hits 0, you can then choose to unstake your deposit. Total votes when staking IOTX can be calculated with the formula below:

$$
votes = deposited\_iotx + log_{1.2}(lock\_days)
$$

**Note:** Note: Once the stake duration has expired and you perform the unstake action, **the unstaking process takes an additional 3 days**. Following this, you can perform the "withdraw" action to get your tokens to your wallet.

### Enable Stake Lock (former "Auto-stake") <a href="#stake-lock-auto-stake" id="stake-lock-auto-stake"></a>

When you turn stake-lock ON, you pause your lock duration countdown until you decide to turn it OFF and the countdown resumes. The benefit of stake-lock is that you earn more bonus votes/rewards while it is on. After you turn the stake-lock OFF, your stake duration will resume counting down to 0.

Remember, if you turn stake-lock back ON at any point during your countdown, your stake duration will restart to the original duration for which you set it. (i.e. If on day 50 of your 100 day stake duration, you choose to turn stake-lock ON. When you turn it OFF, you must now wait 100 days to unstake).

## Additional Resources <a href="#additional-resources" id="additional-resources"></a>

* [Voter Handbook](https://docs.google.com/presentation/d/e/2PACX-1vSrTSl2o2or7TJNpmjcOd57fbHgYGIwTJg0gJmkGuL5Ci5l3hgW1WMDVpzsleA9Vk5gN5OyjAe9osy-/pub?start=false\&loop=false\&delayms=3000\&slide=id.p1\&ref=iotex.io)
* Community Guide: [Maximizing Returns On Your $IOTX](https://community.iotex.io/t/maximizing-returns-on-your-iotx/1634?ref=iotex.io)
* Want to become a delegate? Check out the [Delegates Handbook](https://onboard.iotex.io/hardware/delegates?ref=iotex.io)
* Join the [IoTeX Community Forum](https://community.iotex.io/?ref=iotex.io) for more discussions, questions, and updates!
