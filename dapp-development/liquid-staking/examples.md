# Examples

Below are a few examples demonstrating how to interact with the contracts using TypeScript and the `ethers` library.

### Prerequisites

1. Ensure you have Node.js and npm installed.
2. Familiarity with TypeScript and blockchain concepts.

### Step 1: Setting up the Environment

First, install the `ethers` in your Typescript project library using **npm**:

```bash
npm install ethers
```

### Step 2: Initializing the Contracts

Before any interaction, initialize the contracts:

```typescript
import { ethers } from 'ethers';

// Depending on your network (mainnet or testnet), use the respective address:
const systemContractMainnet = new ethers.Contract(
    "0x68Db92A6a78A39DcAFf1745Da9E89E230eF49D3D",
    systemStakingContractABI,
    provider
);

// If using testnet:
const systemContractTestnet = new ethers.Contract(
    "0x52ab0fe2c3a94644de0888a3ba9ea1443672e61f",
    systemStakingContractABI,
    provider
);

// Initialize the Staking Read Contract (common for both networks):
const stakingReadContract = new ethers.Contract(
    "0x04c22afae6a03438b8fed74cb1cf441168df3f12",
    stakingReadContractABI,
    provider
);
```

### Step 3: Querying Available Bucket Types

Check the activated bucket types:

```typescript
async function getBucketTypes() {
    const types = await stakingReadContract.contractStakeBucketTypes("0x52ab0fe2c3a94644de0888a3ba9ea1443672e61f");
    console.log("Available bucket types:", types);
}
```

### Step 4: Creating an NFT Bucket

To create a stake bucket of 10,000 IOTX for a 30-day duration:

```typescript
async function createBucket() {
    const tx = await systemContract.stake(
        518400, // 30day equivalent in IoTeX blocks
        "io1tfke5nfwryte6nultpmqefadgm0dsahm2gm63k", // delegate profile address
        {value: 10000} // stake deposit amount in IOTX
    );
    await tx.wait();
    console.log("Bucket created successfully!");
}
```

### Step 5: Expanding a Bucket

Increase the stake amount a snd duration of an existing bucket:

```typescript
async function expandBucket() {
    const tx = await systemContract.expandBucket(
        1, // Bucket token id
        20000, // new amount (final)
        1036800, // new duration (60 days)
        {value: 10000} // new amount supplied
    );
    await tx.wait();
    console.log("Bucket expanded successfully!");
}
```

### Step 6: Transferring a Bucket

Transferring a bucket is akin to transferring an ERC-721 token:

```typescript
async function transferBucket() {
    const tx = await systemContract.transferFrom(
        "io1tfke5nfwryte6nultpmqefadgm0dsahm2gm63k", // from address
        "io12mgttmfa2ffn9uqvn0yn37f4nz43d248l2ga85", // to address
        1 // bucket token id
    );
    await tx.wait();
    console.log("Bucket transferred successfully!");
}
```

### Step 7: Unlocking, Unstaking, and Withdrawing

After creating a bucket, you might need to unlock, unstake, or even withdraw:

```typescript
async function unlockBucket() {
    const tx = await systemContract.unlock(1); // pass the token id
    await tx.wait();
    console.log("Bucket unlocked successfully!");
}

async function unstakeBucket() {
    const tx = await systemContract.unstake(1); // pass the token id
    await tx.wait();
    console.log("Bucket unstaked successfully!");
}

async function withdraw() {
    const tx = await systemContract.withdraw(
        1, // Token id
        "io1tfke5nfwryte6nultpmqefadgm0dsahm2gm63k" // Recipient address
    );
    await tx.wait();
    console.log("Withdrawal successful!");
}
```

### Conclusion

These are the foundational steps for interacting with IIP-13 contracts, that allows the creation of Liquid Staking solutions. Liquid staking allows users to access the benefits of staking in a blockchain network while still maintaining liquidity and flexibility over their staked assets, which create a more attractive and versatile staking experience.

For more advanced operations and deeper insights, refer to the IIP-13 official documentation and the contract's source code.

\
