# Staking & Voting

### Create Bucket for Voting

`Usage: ioctl stake2 create AMOUNT_IOTX CANDIDATE_NAME STAKE_DURATION [DATA] [--auto-stake] [-s SIGNER] [-n NONCE] [-l GAS_LIMIT] [-p GASP_RICE] [-P PASSWORD] [-y]`

```
➜  ioctl stake2 create 130 robotbp00000 7 --auto-stake -s tmp2
Enter password #io120au9ra0nffdle04jx2g5gccn6gq8qd4fy03l4:


version: 1  nonce: 420  gasLimit: 10000  gasPrice: 0.000001 IOTX
senderAddress: io120au9ra0nffdle04jx2g5gccn6gq8qd4fy03l4 (tmp)
version: 1
nonce: 420
gasLimit: 10000
gasPrice: "1000000000000"
stakeCreate: <
  candidateName: "robotbp00000"
  stakedAmount: "130000000000000000000"
  stakedDuration: 7
  autoStake: true
>
senderPubKey: 0422346c407294b5e37487395f193faa48dabfc2225ab33fe47b335299f46505b1689f0d96fd53bd19971fe47f310669cf6260dcdc23318454814a4fe904f4d384
signature: 64cb75de95732ab1f3bf04fbfa8449d05a4d7a1115f8aad07b369316dbff75c54ba1d3c66ead9ac26e57c9212f73c9009eba11260d5c2f89ed51ff68b56e54b000

Please confirm your action.


Options: yes
Quit for anything else.
yes
Action has been sent to blockchain.
Wait for several seconds and query this action by hash:30aa10f565f425b0d7b34b57cbf4b22a164b8eb391c1c24bcdc012cabc09a513
```

### Add more IOTX to a Bucket

`Usage: ioctl stake2 add BUCKET_INDEX AMOUNT_IOTX [DATA] [-s SIGNER] [-n NONCE] [-l GAS_LIMIT] [-p GAS_PRICE] [-P PASSWORD] [-y]`

```
➜  ioctl stake2 add 56 102 -s tmp2 -y
Enter password #io120au9ra0nffdle04jx2g5gccn6gq8qd4fy03l4:

Action has been sent to blockchain.
Wait for several seconds and query this action by hash:a51805dbca3046c62f3dd14366594bdd9aabdbe02aa394712556c801bc206359
```

### Renew a Bucket

`Usage: ioctl stake2 renew BUCKET_INDEX STAKE_DURATION [DATA] [--auto-stake] [-s SIGNER] [-n NONCE] [-l GAS_LIMIT] [-p GAS_PRICE] [-P PASSWORD] [-y]`

```
➜   ioctl stake2 renew 56 7 -s tmp2
Enter password #io120au9ra0nffdle04jx2g5gccn6gq8qd4fy03l4:


version: 1  nonce: 424  gasLimit: 10000  gasPrice: 0.000001 IOTX
senderAddress: io120au9ra0nffdle04jx2g5gccn6gq8qd4fy03l4 (tmp)
version: 1
nonce: 424
gasLimit: 10000
gasPrice: "1000000000000"
stakeRestake: <
  bucketIndex: 56
  stakedDuration: 7
>
senderPubKey: 0422346c407294b5e37487395f193faa48dabfc2225ab33fe47b335299f46505b1689f0d96fd53bd19971fe47f310669cf6260dcdc23318454814a4fe904f4d384
signature: 1e8683119f9ccb041f53f4da8cdc16681fc1e542825e44a0e576f6783600176a1eb106b1eed500694cc3bff88b19fbd8cfd6c921faabb99440c15dc0272a09d400

Please confirm your action.


Options: yes
Quit for anything else.
yes
Action has been sent to blockchain.
Wait for several seconds and query this action by hash:c6acfec04e0a6a623713f928bdbe94eb573a6d52227241e0595509cea44728ab
```

### Change Candidate Of Bucket <a href="#change-candidate-of-bucket" id="change-candidate-of-bucket"></a>

`Usage: ioctl stake2 change CANDIDATE_NAME BUCKET_INDEX [DATA] [-s SIGNER] [-n NONCE] [-l GAS_LIMIT] [-p GAS_PRICE] [-P PASSWORD] [-y]`

```
➜   ioctl stake2 change robotbp00001 56 -s tmp2
Enter password #io120au9ra0nffdle04jx2g5gccn6gq8qd4fy03l4:


version: 1  nonce: 425  gasLimit: 10000  gasPrice: 0.000001 IOTX
senderAddress: io120au9ra0nffdle04jx2g5gccn6gq8qd4fy03l4 (tmp2)
version: 1
nonce: 425
gasLimit: 10000
gasPrice: "1000000000000"
stakeChangeCandidate: <
  bucketIndex: 56
  candidateName: "robotbp00001"
>
senderPubKey: 0422346c407294b5e37487395f193faa48dabfc2225ab33fe47b335299f46505b1689f0d96fd53bd19971fe47f310669cf6260dcdc23318454814a4fe904f4d384
signature: 03cd6ccc8c7adf739ea34666ef87cde19d35f3a1938d3aba921a713f8d7b26a90f7e07c3557aec67cc81c82ddf2b2e5d316016da4fcda46e4c93920e53a5ca5701

Please confirm your action.


Options: yes
Quit for anything else.
yes
Action has been sent to blockchain.
Wait for several seconds and query this action by hash:2ee5a6bb764c502d9a8a016d71d83e8b610f4bade1bb0207ec97108a2934a1f6
```

### Transfer Ownership Of Bucket

`Usage: ioctl stake2 transfer (ALIAS|VOTE_ADDRESS) BUCKET_INDEX [DATA] [-s SIGNER] [-n NONCE] [-l GAS_LIMIT] [-p GAS_PRICE] [-P PASSWORD] [-y]`

```
➜  ioctl stake2 transfer daddypig 56 -s tmp2
Enter password #io120au9ra0nffdle04jx2g5gccn6gq8qd4fy03l4:


version: 1  nonce: 426  gasLimit: 10000  gasPrice: 0.000001 IOTX
senderAddress: io120au9ra0nffdle04jx2g5gccn6gq8qd4fy03l4 (tmp)
version: 1
nonce: 426
gasLimit: 10000
gasPrice: "1000000000000"
stakeTransferOwnership: <
  bucketIndex: 56
  voterAddress: "io1gh439pm67d4cwxt882xpylj75klys6esepml60"
>
senderPubKey: 0422346c407294b5e37487395f193faa48dabfc2225ab33fe47b335299f46505b1689f0d96fd53bd19971fe47f310669cf6260dcdc23318454814a4fe904f4d384
signature: 7ff14a55d71307b221675f8c5b21ca0a3390bace47c855cdaa5d8fca00287601714d2076a270e74fcef235571bd2bd97d85e06ee3cc46473ca94c7ad34702cc200

Please confirm your action.


Options: yes
Quit for anything else.
yes
Action has been sent to blockchain.
Wait for several seconds and query this action by hash:f23774c081a0a66c3f3830ca64e1efe669bb0cc7ea7815774294824f9c1b4c15
```

### Release a Over-Time Bucket <a href="#release-a-over-time-bucket" id="release-a-over-time-bucket"></a>

`Usage: ioctl stake2 release BUCKET_INDEX [DATA] [-c ALIAS|CONTRACT_ADDRESS] [-s SIGNER] [-n NONCE] [-l GAS_LIMIT] [-p GASPRICE] [-P PASSWORD] [-y]`

```
➜   ioctl stake2 release 1
Enter password #ioxxx...xxx:
...
...
Action has been sent to blockchain.
Wait for several seconds and query this action by hash:iotexscan.io/action/xxx...xxx
```

### Withdraw IOTX From a Released Bucket <a href="#withdraw-iotx-from-a-released-bucket" id="withdraw-iotx-from-a-released-bucket"></a>

`Usage: ioctl stake2 withdraw BUCKET_INDEX [DATA] [-c ALIAS|CONTRACT_ADDRESS] [-s SIGNER] [-n NONCE] [-l GAS_LIMIT] [-p GASPRICE] [-P PASSWORD] [-y]`

```
➜   ioctl stake2 withdraw 1
Enter password #ioxxx...xxx:
...
...
Action has been sent to blockchain.
Wait for several seconds and query this action by hash:iotexscan.io/action/xxx...xxx
```

### Register Candidate <a href="#register-candidate" id="register-candidate"></a>

`Usage: ioctl stake2 register NAME (ALIAS|OPERATO_ADDRESS) (ALIAS|REWARD_ADDRESS) (ALIAS|OWNER_ADDRESS) AMOUNT_IOTX STAKE_DURATION [DATA] [--auto-stake] [-s SIGNER] [-n NONCE] [-l GAS_LIMIT] [-p GAS_PRICE] [-P PASSWORD] [-y]`

```
➜   ioctl stake2 register pig tmp2 tmp2 tmp2 1000000 7 -s tmp2
Enter password #io120au9ra0nffdle04jx2g5gccn6gq8qd4fy03l4:


version: 1  nonce: 428  gasLimit: 10000  gasPrice: 0.000001 IOTX
senderAddress: io120au9ra0nffdle04jx2g5gccn6gq8qd4fy03l4 (tmp)
version: 1
nonce: 428
gasLimit: 10000
gasPrice: "1000000000000"
candidateRegister: <
  candidate: <
    name: "pig"
    operatorAddress: "io120au9ra0nffdle04jx2g5gccn6gq8qd4fy03l4"
    rewardAddress: "io120au9ra0nffdle04jx2g5gccn6gq8qd4fy03l4"
  >
  stakedAmount: "1000000000000000000000000"
  stakedDuration: 7
  ownerAddress: "io120au9ra0nffdle04jx2g5gccn6gq8qd4fy03l4"
>
senderPubKey: 0422346c407294b5e37487395f193faa48dabfc2225ab33fe47b335299f46505b1689f0d96fd53bd19971fe47f310669cf6260dcdc23318454814a4fe904f4d384
signature: 3839e559a155e34900e2fc7b9cb45c772c1eac16ce9b2a84d4c033de054c8841062825fe368c984c1a367c1e16c16cfe4518335db346b3ab47277378fc0aa29c00

Please confirm your action.


Options: yes
Quit for anything else.
yes
Action has been sent to blockchain.
Wait for several seconds and query this action by hash:9571ad35b0184ad75eaabe539d57513f37fac74b9f605c172fbc28b760d256df
```

### Update Candidate Information <a href="#update-candidate-information" id="update-candidate-information"></a>

`Usage: ioctl stake2 update NAME (ALIAS|OPERATOR_ADDRESS) (ALIAS|REWARD_ADDRESS) [-s SIGNER] [-n NONCE] [-l GAS_LIMIT] [-p GAS_PRICE] [-P PASSWORD] [-y]`

```
➜   ioctl stake2 update pig tmp2 tmp2 -s tmp2
Enter password #io120au9ra0nffdle04jx2g5gccn6gq8qd4fy03l4:


version: 1  nonce: 429  gasLimit: 10000  gasPrice: 0.000001 IOTX
senderAddress: io120au9ra0nffdle04jx2g5gccn6gq8qd4fy03l4 (tmp)
version: 1
nonce: 429
gasLimit: 10000
gasPrice: "1000000000000"
candidateUpdate: <
  name: "pig"
  operatorAddress: "io120au9ra0nffdle04jx2g5gccn6gq8qd4fy03l4"
  rewardAddress: "io120au9ra0nffdle04jx2g5gccn6gq8qd4fy03l4"
>
senderPubKey: 0422346c407294b5e37487395f193faa48dabfc2225ab33fe47b335299f46505b1689f0d96fd53bd19971fe47f310669cf6260dcdc23318454814a4fe904f4d384
signature: e403da0e9c928cbedbbba4ab97d9cc57a1f207a4c72c8e44bbfdf0a90a3ee01e48a2ca1d9e6bc15f6d9b4230d592f1577bb8ad8a1c9529ada986edfec6662c1801

Please confirm your action.


Options: yes
Quit for anything else.
yes
Action has been sent to blockchain.
Wait for several seconds and query this action by hash:c6daaedee325d339e2eba15b76646329c940c0f07ebe9c13cd1f3288ee319a5d
```
