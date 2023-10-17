# Liquid Staking Solutions

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

In this section we explore in details how to interact with the SystemStaking contract from another contract to enable liquid staking functionalities.

### Setting up the Environment

1. When developing your Liquid Staking contract, ensure you include the `IStakingSource` contract interface from the [`IIP13` repository](https://github.com/iotexproject/iip13-contracts).
2. Ensure your client contract implements `IERC721Receiver`, as it will receive the NFT Bucket from the `SystemStaking` contract upon staking creation.

```solidity
import "./ISystemStaking.sol"; 
import "@openzeppelin/contracts/token/ERC721/IERC721Receiver.sol";

contract MyLiquidStaking is IERC721Receiver {
    // Holds the System staking contract address
    ISystemStaking public SystemStakingContract;

    // Constructor
    // Address for IoTeX Testnet: 0x52ab0fe2c3a94644de0888a3ba9ea1443672e61f
    // Address for IoTeX Mainnet: 0x68db92a6a78a39dcaff1745da9e89e230ef49d3d
    constructor(address _SystemStakingContractAddress) {
        // Set the System staking contract address
        SystemStakingContract = ISystemStaking(_SystemStakingContractAddress);
    ...
```

### Staking IOTX from your Contract

The SystemStaking contract provides three stake functions that enable the creation of a new staking bucket in different scenarios. Each of them returns the id assigned to the newly created bucket, which coincides with the NFT token id:

```solidity
// Create a single staking bucket with a specific duration and delegate
function stake(uint256 _duration, address _delegate) external payable returns (uint256);
// Create multiple staking buckets, each with the same amount and duration, for different delegates:
function stake(uint256 _amount, uint256 _duration, address[] memory _delegates) external payable returns (uint256);
// Create several staking buckets, each with the same amount and duration, all assigned to a single delegate
function stake(uint256 _amount, uint256 _duration, address _delegate, uint256 _count) external payable returns (uint256);
```

For instance, to generate a new NFT bucket with a 100 IOTX deposit, assigned to an eligible IoTeX delegate, you would use:

```solidity
uint256 tokenId = 
    SystemStakingContract.stake{value: msg.value}(
    1572480, // 91 days in IoTeX blocks
    0xCD397ac1364676d8553D9ce78e4B0d27f236926d // Owner address of the delegate
    );
```

<details>

<summary><strong>Note on Staking Amount and Duration</strong></summary>

When creating a new staking bucket, it's important to ensure that the chosen stake amount and duration match one of the combinations the `SystemStaking` contract supports, otherwise the action will revert. These combinations are called "Bucket Types". For the best user experience, consider fetching the list of all supported bucket types from your dApp frontend to guide users during the staking process.

To obtain the current list of bucket types, use the following methods from the `SystemStaking` contract:

```solidity
// Get the total number of bucket types
function numOfBucketTypes() external view returns (uint256);
// Retrieve the paginated list of supported bucket types
function bucketTypes(uint256 _offset, uint256 _size) external view returns (BucketType[] memory);
```

</details>

<details>

<summary><strong>Note on Delegate Owner Addresses</strong></summary>

When creating a new staking bucket or changing the delegate of an existing bucket, it's important to input the delegate's "owner address," also referred to as the delegate's "profile address." This address uniquely identifies each IoTeX delegate. Ensure that the addresses you utilize actually belong to delegates and that they are eligible (meaning their self-stake amount is at least 1.2M IOTX). Failing to do so will cause a contract action revert.

To facilitate this process in your frontend, leverage the IoTeX Staking virtual contract to access details regarding delegate names, addresses, and self-staking data. The relevant method is listed below, but for comprehensive details, please [refer to the IoTeX Staking Integration section -> ](iotex-staking-integration.md)

```solidity
function candidates(uint32 offset, uint32 limit) external view returns (IStaking.Candidate[] memory);
```

</details>

### Changing the StakeLock status

When a new staking bucket is created using the SystemStaking conatrct, the default state of teh StakeLock option is enabled. In this situation, the bucket is locked for the bucket's lock duration time, and will persist in this state without the lock duration to decrease. While enabling the StakeLock option guarantees increased rewards, in order the be able to unstake a bucket at a specific time, you must ensure that the StakeLock option has been disabled for the bucket ahead of time (exactly the number of days of the lock duration).&#x20;

```solidity
// Disables StakeLock for a bucket
function unlock(uint256 _tokenId) external
// Disables StakeLock for multiple buckets (must be owned by the same owner)
function unlock(uint256[] calldata _tokenIds) external
// Enables StakeLock for a bucket and sets a new lock duration (must be >= to the remaining lock time)
function lock(uint256 _tokenId, uint256 _duration) external;
// Enables StakeLock for multiple bucket and sets a new lock duration (same for all)
function lock(uint256[] calldata _tokenIds, uint256 _duration) external;
```

### Unstaking a bucket

Before you can withdraw the IOTX deposit, unstaking a bucket is a prerequisite. For a bucket to qualify for unstaking, it must be in the "unlocked" status. This indicates that the `StakeLock` option for that specific bucket must have remained deactivated throughout the entire lock duration of the bucket. Once initiated, the unstaking process lasts 3 days (equivalent to 51,840 IoTeX blocks). During this period, the bucket remains locked, does not generate staking rewards, and is immune to any operations.

```solidity
// Unstakes a bucket
function unstake(uint256 _tokenId) external;
// Unstakes multiple buckets
function unstake(uint256[] calldata _tokenIds) external;
```

### Withdrawing a bucket

Before you can withdraw a deposit, it must have completed the unstaking process.

```solidity
// Withdraws a staking bucket deposit to a certain recipient address
function withdraw(uint256 _tokenId, address payable _recipient) external;
// Withdraws multiple staking bucket deposits to a certain recipient address
function withdraw(uint256[] calldata _tokenIds, address payable _recipient) external;
```

### More operations

```solidity
function blocksToUnstake(uint256 _tokenId) external view returns (uint256);
function blocksToWithdraw(uint256 _tokenId) external view returns (uint256);
function bucketOf(uint256 _tokenId) external view returns (uint256, uint256, uint256, uint256, address);
function merge(uint256[] calldata tokenIds, uint256 _newDuration) external payable;
function expandBucket(uint256 _tokenId, uint256 _newAmount, uint256 _newDuration) external payable;
function changeDelegate(uint256 _tokenId, address _delegate) external;
function changeDelegates(uint256[] calldata _tokenIds, address _delegate) external;
function lockedVotesTo(address[] calldata _delegates) external view returns (uint256[][] memory counts_);
function unlockedVotesTo(address[] calldata _delegates) external view returns (uint256[][] memory counts_);
```

## Conclusion

These are the foundational steps for interacting with IIP-13 contracts, that allows the creation of Liquid Staking solutions. Liquid staking allows users to access the benefits of staking in a blockchain network while still maintaining liquidity and flexibility over their staked assets, which create a more attractive and versatile staking experience.

For more advanced operations and deeper insights, please refer to the original [IIP-13 proposal](https://github.com/iotexproject/iips/blob/master/iip-13.md) and the [contract's source code](https://github.com/iotexproject/iip13-contracts).

