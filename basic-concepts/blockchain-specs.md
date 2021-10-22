# Blockchain Specs

## Quick specs of the IoTeX Blockchain

### Block Time

5-Second Block Time

### Action Confirmation

**7.5 Seconds** on average. The fastest possible confirmation time is **5 Seconds**.

### Action Finality

**1-Block finality **for all blockchain actions.

### Transaction Validation

Randomized Delegated Proof of Stake ([Roll-DPoS](https://files.iotex.io/publications/Academic\_Paper\_Yellow\_Paper.pdf))&#x20;

### Consensus Algorithm

Practical Byzantine Fault Tolerant (PBFT)

### Chain IDs

A **Chain ID** is a unique number assigned to different, independent IoTeX Blockchains. For example, IoTeX Mainnet chain has`Chain ID = 1`, while IoTeX Testnet has `Chain ID = 2`. Chain IDs in IoTeX are used for security reasons by including them in transaction signatures to prevent _transaction replay_ attacks on different networks.

#### List of IoTeX Chain ID's

All IoTeX-based blockchains should adopt this _Chain ID Mechanism_ by replacing `CHAIN ID` with a different and **unique** value. All testnet, consortium, and any IoTeX-cloned chains are encouraged to do the same:
