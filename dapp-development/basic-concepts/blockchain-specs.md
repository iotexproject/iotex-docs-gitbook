# Blockchain Specs

<details>

<summary>Block Time</summary>

5-Second Block Time

</details>

<details>

<summary>Action Confirmation</summary>

**7.5 Seconds** on average. The fastest possible confirmation time is **5 Seconds**.

</details>

<details>

<summary>Action Finality</summary>

**1-Block finality** for all blockchain actions.

</details>

<details>

<summary>Transaction Validation</summary>

Randomized Delegated Proof of Stake ([Roll-DPoS](https://files.iotex.io/publications/Academic\_Paper\_Yellow\_Paper.pdf))&#x20;

</details>

<details>

<summary>Consensus Algorithm</summary>

Practical Byzantine Fault Tolerant (PBFT)

</details>

<details>

<summary>Chain IDs</summary>

A **Chain ID** is a unique number assigned to different, independent IoTeX Blockchains. For example, IoTeX Mainnet chain has`Chain ID = 1`, while IoTeX Testnet has `Chain ID = 2`. Chain IDs in IoTeX are used for security reasons by including them in transaction signatures to prevent _transaction replay_ attacks on different networks.

</details>

<details>

<summary>List of IoTeX Chain IDs</summary>

All IoTeX-based blockchains should adopt this _Chain ID Mechanism_ by replacing `CHAIN ID` with a different and **unique** value.&#x20;

All testnet, consortium, and any IoTeX-cloned chains are encouraged to do the same.

</details>
