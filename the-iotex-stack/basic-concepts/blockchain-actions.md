# Blockchain Actions

Any blockchain is bootstrap from an initial (_genesis_) state, which is then changed over time through transactions, or **Actions** as they are called in IoTeX. An action is fundamentally a _packet of data_, signed by a blockchain account, that instructs the blockchain to make some type of change to the distributed ledger. The action can be sent to any blockchain node acting as a gateway, that in turn broadcasts it to the entire network of nodes for verification and, eventually it get applied and stored forever in the Ledger.

In IoTeX there are different types of Actions, depending on the type of operation that is required to perform:

<details>

<summary>Transfer Action</summary>

A transfer is an action initiated by an account, intended to _transfer_ a certain amount of IOTX tokens owned by that account (_sender_) into another account (_recipient_).

</details>

<details>

<summary>Execution Action</summary>

An execution is an action initiated by an account, intended to run the code associated with a smart contract account.

</details>

<details>

<summary>Governance Actions</summary>

Governance actions are low level actions between an account and the blockchain itself, intended to manage the voting mechanism, delegate registrations and rewards.

* **GrantReward** is the action initiated by the blockchain, to grant either block or epoch reward to a delegate
* **ClaimFromRewardingFund** is the action initiated by an account to claim delegate reward from the granted rewards fund
* **DepositToRewardingFund** is the action initiated by the blockchain to deposit a delegate reward to the rewarding fund
* **CandidateRegister** is the action to register a candidate
* **CandidateUpdate** is the action to update a candidate data
* **CreateStake** defines the action of stake creation
* **Restake** defines the action of stake again with different options
* **DepositToStake** defines the action of stake add deposit
* **TransferStake** defines the action of transfering stake ownership to another account
* **Unstake** defines the action of unstake
* **WithdrawStake** defines the action of stake withdraw

</details>

#### Find the structure for all IoTeX Actions in the protobuf definition on GitHub:

{% embed url="https://github.com/iotexproject/iotex-proto/blob/master/proto/types/action.proto" %}
