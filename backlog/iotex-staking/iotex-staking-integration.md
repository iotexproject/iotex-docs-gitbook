# IoTeX Staking Integration

In this section, we'll guide you through the process of integrating IoTeX Staking into staking platforms that offer Stake as a Service. Developers have two options for integrating IoTeX Staking into their systems: utilizing the Ethereum RPC API or IoTeX's native protocol. We recommend the Ethereum JSON RPC API because it offers compatibility with Ethereum development libraries and tools, making it the preferred choice for most developers.

## **Utilizing the Ethereum API**

With the adoption of the [IIP12](https://github.com/iotexproject/iips/blob/master/iip-12.md) improvement proposal, it became possible to perform staking actions on the IoTeX blockchain via Ethereum JSON RPC calls. This advancement allows for the creation and management of staking using regular Ethereum transactions. These transactions can be easily created with tools such as Web3.js and can be signed by wallets like Metamask.

### **How it works**

The IoTeX blockchain allows staking actions through standard Ethereum API calls via a mechanism known as a "Virtual Contract". A virtual contract is essentially a designated blockchain address pre-set within the IoTeX protocol. Any transactions directed to this address are undergo a dedicated process by the protocol. Specifically, these transactions are expected to contain a payload which holds the encoded native message for the desired staking operation. The IoTeX protocol then decodes and performs the specific action included within the Ethereum transaction payload.

[Visit the original IIP12 Proposal ->](https://github.com/iotexproject/iips/blob/master/iip-12.md)

### The Staking Virtual Contract

The address below is the pre-set address designated to symbolize the native staking contract. Ethereum transactions directed to this address will be converted into native staking actions by the IoTeX protocol upon decoding the actual staking action from the transaction payload.

To facilitate the task of reading the status of staking deposits on IoTeX through the Ethereum API, the same address can be utilized as a "Read Contract" to perform any type of read action on the status of staking.

[Source Code](https://github.com/iotexproject/iip12-contracts/blob/learn/interface/NativeStaking.sol) | [ABI](https://github.com/iotexproject/iip12-contracts/blob/learn/abi/NativeStaking.abi)&#x20;

<table><thead><tr><th width="203">Network</th><th width="505">Address</th></tr></thead><tbody><tr><td>Testnet &#x26; Mainnet</td><td><code>0x04c22afae6a03438b8fed74cb1cf441168df3f12</code></td></tr></tbody></table>

{% hint style="info" %}
It's important to note that this isn't a conventional smart contract that is deployed and resides on the blockchain with a specific contract address. Rather, it's a pre-defined address recognized solely by the blockchain protocol, which processes incoming transactions in a unique manner. Its sole purpose is to facilitate access to the IoTeX protocol's staking actions for an Ethereum client. As a result, while you can send execution or read transactions to this address using the Ethereum JSON RPC API, **you cannot call the same functions from another smart contract**. This is because the virtual contract isn't visible to the EVM.
{% endhint %}

## Examples

Interacting with the virtual contract via JSON-RPC is no different from interacting with a real EVM contract. Here are some examples on how to interact with IoTeX Native staking using the IIP12 virtual contract via a web3 client. For these demonstrations, we'll utilize the `ethers.js` library.

### **Retrieving the Contract Interface Using Metamask**

```typescript
import ethers from "ethers";

const provider = new ethers.providers.Web3Provider(window.ethereum);
const signer = provider.getSigner();
// Make sure to assign the ABI to the abi variable
const stakingContract = new ethers.Contract('0x04C22AfaE6a03438b8FED74cb1Cf441168DF3F12', abi, signer);
```

### Creating a new stake

The example below creates a new staking with a deposit amount of 100 IOTX, a duration of 91 days and the StakeLock option enabled. The resulting bucket of votes is assigned to the delegate "delegateName".

**Contract function signature:**

```javascript
async function createStake(candName: string, amount: number, duration: number, autoStake: boolean, data: string[])
```

**Code:**

```javascript
// 100 IOTX = 100 * 1e18
const transaction = await stakingContract.createStake('delegatename', '100000000000000000000', 91, true, []);
console.log(transaction); 
```

The resulting log would look like the following. Notice that, if the transaction is successful, then `receipt.Status` will equal 1:

```json
{
    "receipt": {
        "to": "0x04C22AfaE6a03438b8FED74cb1Cf441168DF3F12",
        "from": "0x1745a52aA2939422D603FB5035ECb0db686a647c",
        "contractAddress": null,
        "transactionIndex": 1,
        "gasUsed": {
            "type": "BigNumber",
            "hex": "0x2710"
        },
        "logsBloom": "0x00000000000008000000000000004000000000000002000000000000000000000000000000000000000000000000000000800000000040000000000008020000000000000000000000000000000000000000000000000000000040000100000000000080000000000000004000000000000000000000000000000000000000010000200080000000080200000000000000000000000000000000000000000000000000000000000000000000010000000000000000001000800000000000000000000000000000000000000000000000000000000000000000000000000000000000020240000000000000000000000000200000000008000000000000000000",
        "blockHash": "0x6c3532bae6db560a154018888f77b6d19ec0bc8cbb8c15614c432fd811781e26",
        "transactionHash": "0xb64b6c3cb492293d53a0e10fe582edbc7506960e4ae45fd13194eb9cd06f98a1",
        "logs": [
            {
                "transactionIndex": 1,
                "blockNumber": 26295171,
                "transactionHash": "0xb64b6c3cb492293d53a0e10fe582edbc7506960e4ae45fd13194eb9cd06f98a1",
                "address": "0x04C22AfaE6a03438b8FED74cb1Cf441168DF3F12",
                "topics": [
                    "0x0000000000000000000000000000000000000000006372656174655374616b65"
                ],
                "data": "0x",
                "logIndex": 1,
                "blockHash": "0x6c3532bae6db560a154018888f77b6d19ec0bc8cbb8c15614c432fd811781e26"
            }
        ],
        "blockNumber": 26295171,
        "confirmations": 2,
        "cumulativeGasUsed": {
            "type": "BigNumber",
            "hex": "0x2710"
        },
        "status": 1,
        "type": 0,
        "byzantium": true
    },
    "hash": "0xb64b6c3cb492293d53a0e10fe582edbc7506960e4ae45fd13194eb9cd06f98a1"
}
*/
```

### Unstake a deposit

**Contract function signature:**

```javascript
function unstake(bucketIndex: string, data: string[])
```

**Code:**

```javascript
const transaction = await stakingContract.unstake('1', []);
```

### Withdraw an unstaked deposit

**Contract function signature:**

```javascript
function withdrawStake(bucketIndex: string, data: string[])
```

**Code:**

```javascript
const transaction = await stakingContract.withdrawStake('1', []);
```

### Read the details of a bucket

**Contract function signature:**

```javascript
function bucketsByIndexes(indexes: string[])
```

**Code:**

```javascript
const response = await stakingContract.bucketsByIndexes(['1']);
console.log(response); 
```

**Example log output:**

```json
[
    [
        {
            "0": {
                "type": "BigNumber",
                "hex": "0xd9"
            },
            "1": "0xB7860456d0918B14d75EDb53216F5C9eb22859D8",
            "2": {
                "type": "BigNumber",
                "hex": "0x056bc75e2d63100000"
            },
            "3": 2,
            "4": {
                "type": "BigNumber",
                "hex": "0x64b60297"
            },
            "5": {
                "type": "BigNumber",
                "hex": "0x65236599"
            },
            "6": {
                "type": "BigNumber",
                "hex": "0x00"
            },
            "7": true,
            "8": "0x1745a52aA2939422D603FB5035ECb0db686a647c",
            "index": "1",
            "candidateAddress": "0xB7860456d0918B14d75EDb53216F5C9eb22859D8",
            "stakedAmount": "100000000000000000000",
            "stakedDuration": "2",
            "createTime": "1689649815",
            "stakeStartTime": "1696818585",
            "unstakeStartTime": "0",
            "autoStake": true,
            "owner": "0x1745a52aA2939422D603FB5035ECb0db686a647c"
        }
    ]
]
```

### List the buckets owned by a specific address

**Contract function signature:**

```javascript
function bucketsByVoter(voter: string, offset: string, limit: string)
```

**Code:**

```javascript
const response = await stakingContract.bucketsByVoter('io1zaz6224zjw2z94srldgrtm9smd5x5eruzmulnv', '0', '10000'); 
console.log(response); // Response like following.
```

**Example log output:**

```
[
    [
        {
            "0": {
                "type": "BigNumber",
                "hex": "0xd2"
            },
            "1": "0x5D34b7115124B80863f20CB07D16E403A280C1Ce",
            "2": {
                "type": "BigNumber",
                "hex": "0x056bc75e2d63100000"
            },
            "3": 1,
            "4": {
                "type": "BigNumber",
                "hex": "0x649d4ca7"
            },
            "5": {
                "type": "BigNumber",
                "hex": "0x649d4ca7"
            },
            "6": {
                "type": "BigNumber",
                "hex": "0x00"
            },
            "7": true,
            "8": "0x1745a52aA2939422D603FB5035ECb0db686a647c",
            "index": "210",
            "candidateAddress": "0x5D34b7115124B80863f20CB07D16E403A280C1Ce",
            "stakedAmount": "100000000000000000000",
            "stakedDuration": "1",
            "createTime": "1688030375",
            "stakeStartTime": "1688030375",
            "unstakeStartTime": "0",
            "autoStake": true,
            "owner": "0x1745a52aA2939422D603FB5035ECb0db686a647c"
        },
        {
            "0": {
                "type": "BigNumber",
                "hex": "0xd4"
            },
            "1": "0xC0EdD40Ec22053B849cBb93181dD1651472d6430",
            "2": {
                "type": "BigNumber",
                "hex": "0x056bc75e2d63100000"
            },
            "3": 5,
            "4": {
                "type": "BigNumber",
                "hex": "0x64a2979d"
            },
            "5": {
                "type": "BigNumber",
                "hex": "0x64afb9f5"
            },
            "6": {
                "type": "BigNumber",
                "hex": "0x00"
            },
            "7": false,
            "8": "0x1745a52aA2939422D603FB5035ECb0db686a647c",
            "index": "212",
            "candidateAddress": "0xC0EdD40Ec22053B849cBb93181dD1651472d6430",
            "stakedAmount": "100000000000000000000",
            "stakedDuration": "5",
            "createTime": "1688377245",
            "stakeStartTime": "1689238005",
            "unstakeStartTime": "0",
            "autoStake": false,
            "owner": "0x1745a52aA2939422D603FB5035ECb0db686a647c"
        }
    ]
]
```

## Utilizing the Native API

Unlike other implementations, staking in the IoTeX blockchain is incorporated into the network protocol instead of utilizing contracts. Consequently, developers can utilize the native IoTeX API, through the official [Antenna SDK](../reference/native-development/antenna-overview.md), for staking management purposes.

[Explore the Native SDK on GitHub ->](https://github.com/iotexproject/iotex-antenna)
