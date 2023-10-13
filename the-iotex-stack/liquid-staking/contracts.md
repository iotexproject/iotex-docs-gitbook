# Contracts

{% hint style="success" %}
The full implementation of IIP-13 can be found on GitHub

[https://github.com/iotexproject/iip13-contracts](https://github.com/iotexproject/iip13-contracts)
{% endhint %}

[IIP-13](https://github.com/iotexproject/iips/blob/master/iip-13.md) consists in the implementation of two interrelated contracts:

### **System Staking Contract**

[Source Code](https://github.com/iotexproject/iip13-contracts/blob/main/src/SystemStaking.sol) | [ABI](https://github.com/iotexproject/iip13-contracts/blob/main/abi/SystemStaking.abi)

This is the primary contract responsible for enacting the functionalities laid out in IIP-13. It manages tasks such as creating, modifying, transferring, and querying NFT Buckets.

<table><thead><tr><th width="133">Network</th><th width="453">Address</th></tr></thead><tbody><tr><td>Testnet</td><td><code>0x52ab0fe2c3a94644de0888a3ba9ea1443672e61f</code></td></tr><tr><td>Mainnet</td><td><code>0x68db92a6a78a39dcaff1745da9e89e230ef49d3d</code></td></tr><tr><td></td><td></td></tr></tbody></table>

### **Staking Read Contract**&#x20;

This contract is specifically crafted to speed up the process of querying Buckets.

<table><thead><tr><th width="192">Network</th><th width="453">Address</th></tr></thead><tbody><tr><td>Testnet &#x26; Mainnet</td><td><code>0x04c22afae6a03438b8fed74cb1cf441168df3f12</code></td></tr><tr><td></td><td></td></tr></tbody></table>
