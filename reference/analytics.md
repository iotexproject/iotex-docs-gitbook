# Analytics - GraphQL API

Analytics is an application built upon IoTeX core API which extracts data from IoTeX blockchain and reindexes them for applications to use via a GraphQL web interface. You can use the[ playground here](https://analytics.iotexscan.io).

## Delegate

### Bookkeeping

```text
Usage:
  Bookkeeping gives delegates an overview of the reward distributions to their voters within a range of epochs

Request:
  startEpoch: starting epoch number
  epochCount: epoch count
  delegateName: delegate name
  percentage: percentage of reward distribution
  includeFoundationBonus: whether include foundation bonus as part of the reward distribution
  pagination:
    skip: starting index of displaying reward distribution list
    first: number of reward distributions to display

Response:
  exist: whether the delegate has bookkeeping information within the specified epoch range
  rewardDistribution:
    voterEthAddress: voter’s ERC20 address
    voterIotexAddress: voter’s IoTeX address
    amount: amount of reward distribution
  count:  total number of reward distributions
```

### Productivity

```text
Usage:
  Productivity gives block productivity of producers within a range of epochs

Request:
  startEpoch: starting epoch number
  epochCount: epoch count
  delegateName: producer name

Response:
  exist: whether the delegate has productivity information within the specified epoch range
  production: number of block productions
  expectedProduction: number of expected block productions
```

### Reward

```text
Usage:
  Rewards provides reward detail information for candidates within a range of epochs

Request:
  startEpoch: starting epoch number
  epochCount: epoch count
  delegateName: candidate name

Response:
  exist: whether the delegate has reward information within the specified epoch range
  blockReward: amount of block rewards
  epochReward: amount of epoch rewards
  foundationBonus: amount of foundation bonus

```

### BucketInfo

```text
Usage:
  BucketInfo provides voting bucket detail information for candidates within a range of epochs

Request:
  startEpoch: starting epoch number
  epochCount: epoch count
  delegateName: candidate name

Response:
  exist: whether the delegate has voting bucket information within the specified epoch range
  bucketInfoList:
    epochNumber: epoch number
    bucketInfo:
      voterIotexAddress: voter's IoTeX address
      voterEthAddress: voter’s ERC20 address
      isNative: whether the bucket is native
      votes: voter's votes
      weightedVotes: voter’s weighted votes
      startTime: bucket start time
      remainingDuration: bucket remaining duration
      decay: whether the vote weight decays
      pagination:
        skip: starting index of displaying bucket list
        first: number of buckets to display
    count: total number of buckets in the given epoch for the given delegate
```

### Staking

```text
Usage:
  Staking provides staking information for candidates within a range of epochs

Request:
  startEpoch: starting epoch number
  epochCount: epoch count
  delegateName: candidate name

Response:
  exist: whether the delegate has staking information within the specified epoch range
  stakingInfo:
    epochNumber: epoch number
    selfStaking: candidate’s self-staking amount
    totalStaking: total staking amount
```

### ProbationHistoricalRate

```text
Usage:
  ProbationHistoricalRate provides the rate of probation for a given delegate

Request:
  startEpoch: starting epoch number
  epochCount: epoch count
  delegateName: candidate name

Response:
  probationHistoricalRate: probation historical rate


```

Demo:

```text
Sample Request:

query{
  delegate(startEpoch: 1500, epochCount: 2, delegateName: "blackpool"){
    bookkeeping(percentage: 90, includeFoundationBonus: true){
      exist
      rewardDistribution(pagination: {skip: 0, first: 2}){
        voterEthAddress
        amount
      }
      count
    }
    reward{
      exist
      blockReward
      epochReward
      foundationBonus
    }
    productivity{
      exist
      production
      expectedProduction
    }
    bucketInfo{
      exist
      bucketInfoList{
        epochNumber
        bucketInfo{
          voterEthAddress
          weightedVotes
        }
        count
      }
    }
    staking{
      exist
      stakingInfo{
        epochNumber
        selfStaking
        totalStaking
      }
    }
    probationHistoricalRate
  }
}

Sample Response:

{
  "data": {
    "delegate": {
      "bookkeeping": {
        "exist": true,
        "rewardDistribution": [
          {
            "voterEthAddress": "0x2ed3767cfcbceb42ff5f3642d4df6f851b947073",
            "amount": "249296733398649281"
          },
          {
            "voterEthAddress": "0x6729cdc9172b00ac69f4ce3f98de2eb4d0686925",
            "amount": "5264917870144216244"
          }
        ],
        "count": 4
      },
      "reward": {
        "exist": true,
        "blockReward": "0",
        "epochReward": "329819772195117893866",
        "foundationBonus": "160000000000000000000"
      },
      "productivity": {
        "exist": false,
        "production": "",
        "expectedProduction": ""
      },
      "bucketInfo": {
        "exist": true,
        "bucketInfoList": [
          {
            "epochNumber": 1500,
            "bucketInfo": [
              {
                "voterEthAddress": "2ed3767cfcbceb42ff5f3642d4df6f851b947073",
                "weightedVotes": "12050042619210072913916"
              },
              {
                "voterEthAddress": "6729cdc9172b00ac69f4ce3f98de2eb4d0686925",
                "weightedVotes": "254485824410815439561517"
              },
              {
                "voterEthAddress": "d8e70e5029e5353e8d360365d5273ed329cc4918",
                "weightedVotes": "3203226341724952466266885"
              },
              {
                "voterEthAddress": "d8e70e5029e5353e8d360365d5273ed329cc4918",
                "weightedVotes": "2838636602552620757933254"
              },
              {
                "voterEthAddress": "fe7bcb3676aabe9a6b39cb23f3a5fa41eed7ad1b",
                "weightedVotes": "15000000000000000000000000"
              }
            ],
            "count": 5
          },
          {
            "epochNumber": 1501,
            "bucketInfo": [
              {
                "voterEthAddress": "2ed3767cfcbceb42ff5f3642d4df6f851b947073",
                "weightedVotes": "12050042619210072913916"
              },
              {
                "voterEthAddress": "6729cdc9172b00ac69f4ce3f98de2eb4d0686925",
                "weightedVotes": "254485824410815439561517"
              },
              {
                "voterEthAddress": "d8e70e5029e5353e8d360365d5273ed329cc4918",
                "weightedVotes": "3203226341724952466266885"
              },
              {
                "voterEthAddress": "d8e70e5029e5353e8d360365d5273ed329cc4918",
                "weightedVotes": "2838636602552620757933254"
              },
              {
                "voterEthAddress": "fe7bcb3676aabe9a6b39cb23f3a5fa41eed7ad1b",
                "weightedVotes": "15000000000000000000000000"
              }
            ],
            "count": 5
          }
        ]
      },
      "staking": {
        "exist": true,
        "stakingInfo": [
          {
            "epochNumber": 1500,
            "selfStaking": "5039748000000000000000000",
            "totalStaking": "21308398811307598736675572"
          },
          {
            "epochNumber": 1501,
            "selfStaking": "5039748000000000000000000",
            "totalStaking": "21308398811307598736675572"
          }
        ]
      }
      "probationHistoricalRate": "0.00"
    }
  }
}
```

## Chain

### MostRecentEpoch

```text
Usage:
  MostRecentEpoch gives the latest epoch number

Request:
  N/A

Response:
  mostRecentEpoch: latest epoch number

```

### MostRecentBlockHeight

```text
Usage:
  MostRecentBlockHeight gives the latest block height

Request:
  N/A

Response:
  mostRecentBlockHeight: latest block height

```

### MostRecentTPS

```text
Usage:
  MostRecentTPS gives the latest transactions per second

Request:
  blockWindow: number of last blocks that are backtracked to compute TPS

Response:
  mostRecentTPS: latest transactions per second
```

### NumberOfActions

```text
Usage:
  NumberOfActions gives the number of actions

Request:
  pagination:
    startEpoch: starting epoch number
    epochCount: epoch count

Response:
  exist: whether the starting epoch number is less than the most recent epoch number
  count: number of actions

```

### VotingResultMeta

```text
Usage:
  VotingResultMeta gives the latest metadata of voting result

Request:
  N/A

Response:
  totalCandidates: total number of candidates
  totalWeightedVotes: total weighted votes
  votedTokens: total voted tokens
```

### TotalTransferredTokens

```text
Usage:
  TotalTransferredTokens gives the amount of tokens transferred within a time frame

Request:
  pagination:
    startEpoch: starting epoch number
    epochCount: epoch count

Response:
  totalTransferredTokens: total tranferred tokens

```

Demo:

```text
Sample Request:

query{
  chain{
    mostRecentEpoch
    mostRecentBlockHeight
    mostRecentTPS(blockWindow: 10)
    numberOfActions(pagination: {startEpoch: 1, epochCount: 10}){
      exist
      count
    }
    totalTransferredTokens(pagination:{startEpoch: 1, epochCount: 10})
  }
}

Sample Response:

{
  "data": {
    "chain": {
      "mostRecentEpoch": 1383,
      "mostRecentBlockHeight": 497772,
      "mostRecentTPS": 0,
      "numberOfActions": {
        "exist": true,
        "count": 3622
      }
      "totalTransferredTokens": "10000010000000000000000"
    }
  }
}
```

## Voting

### VotingMeta

```text
Usage:
  VotingMeta provides metadata of voting results

Request:
  startEpoch: starting epoch number
  epochCount: epoch count

Reponse:
  exist: whether the starting epoch number is less than the most recent epoch number
  candidateMeta:
    epochNumber:  epoch number
    consensusDelegates: number of consensus delegates in the epoch
    totalCandidates: number of total delegates in the epoch
    totalWeightedVotes: candidate total weighted votes in the epoch
    votedTokens: total voted tokens in the epoch

```

### CandidateInfo

```text
Usage:
  CandidateInfo provides candidate information

Request:
  startEpoch: starting epoch number
  epochCount: epoch count

Reponse:
  candidateMeta:
    epochNumber:  epoch number
    candidates:
      name: candidate name
      address: canddiate address
      totalWeightedVotes: total weighted votes
      selfStakingTokens: candidate self-staking tokens
      operatorAddress: candidate operator address
      rewardAddress: candidate reward address

```

### RewardSources

```text
Usage:
  RewardSources provides reward sources for voters

Request:
  startEpoch: starting epoch number
  epochCount: epoch count
  voterIotxAddress: voter IoTeX address

Reponse:
  exist: whether the voter has reward information within the specified epoch range
  delegateDistributions:
    delegateName: delegate name
    amount: amount of reward distribution

```

Demo:

```text
Sample Request:

query{
  voting(startEpoch: 1, epochCount: 3){
    exist
    candidateMeta{
      epochNumber
      consensusDelegates
      totalCandidates
      totalWeightedVotes
      votedTokens
    }
  }
}

Sample Response:

{
  "data": {
    "voting": {
      "exist": true,
      "candidateMeta": [
        {
          "epochNumber": 1,
          "consensusDelegates": 36,
          "totalCandidates": 87,
          "totalWeightedVotes": "907521920724956720472322956",
          "votedTokens": "776946421831717811810000000"
        },
        {
          "epochNumber": 2,
          "consensusDelegates": 36,
          "totalCandidates": 87,
          "totalWeightedVotes": "907524412616270399722024013",
          "votedTokens": "776948876231717811810000000"
        },
        {
          "epochNumber": 3,
          "consensusDelegates": 36,
          "totalCandidates": 87,
          "totalWeightedVotes": "907486769208330536874270055",
          "votedTokens": "776953490231717811810000000"
        }
      ]
    }
  }
}

```

Demo:

```text
Sample Request:

query{
	voting(startEpoch: 9760, epochCount: 1){
    votingMeta{
      candidateMeta{
        votedTokens
        totalWeightedVotes
      }
    }
  }
}

Sample Response:

{
  "data": {
    "voting": {
      "votingMeta": {
        "candidateMeta": [
          {
            "votedTokens": "2238183641136247164314750007",
            "totalWeightedVotes": "2540055496482100272999904251"
          }
        ]
      }
    }
  }
}

```

## Account

### ActiveAccounts

```text
Usage:
  ActiveAccounts lists most recently active accounts

Request:
  count: number of account addresses to be queried for active accounts

Response:
  activeAccounts: list of account addresses
```

### OperatorAddress

```text
Usage:
  OperatorAddress finds the delegate's operator address given the delegate's alias name

Request:
  aliasName: delegate's alias name

Response:
  exist: whether the alias name exists
  operatorAddress:  operator address associated with the given alias name
```

### Alias

```text
Usage:
  Alias finds the delegate's alias name given the delegate's operator address

Request:
  operatorAddress: delegate's operator address

Response:
  exist: whether the operator address exists
  aliasName: alias name associated with the given operator address

```

### TotalNumberOfHolders

```text
Usage:
  TotalNumberOfHolders returns total number of IOTX holders so far
Request:
  N/A
Response:
  totalNumberOfHolders: total number of IOTX holders so far

```

### TotalAccountSupply

```text
Usage:
  TotalAccountSupply returns total amount of tokens held by IoTeX accounts
Request:
  N/A
Response:
  totalAccountSupply: total amount of tokens held by IoTeX accounts

```

Demo:

```text
Sample Request:

query{
  account{
    activeAccounts(count: 5)
    operatorAddress(aliasName: "gamefantasy#"){
      exist
      operatorAddress
    }
    alias(operatorAddress: "io1456knehzn9qup8unxlf4q06empz8lqxtp6v5vh"){
      exist
      aliasName
    }
    totalNumberOfHolders
    totalAccountSupply
  }
}

Sample Response:

{
  "data": {
    "account": {
      "activeAccounts": [
        "io17cmrextyfeu4gddwd89g5qncedsnc553dhz7xa",
        "io10reczcaelglh5xmkay65h9vw3e5dp82e8vw0rz",
        "io13xdhg9du56khumz3sg6a3ma5q5kjx7vdlx48x8",
        "io1tf7tu2xt6mpk8s70ahugsx20jqgu9eg6v48qlk",
        "io1xj0u5n20tsqwxh5a3xdtmzuz9wasft0pqjrq8t"
      ],
      "operatorAddress": {
        "exist": true,
        "operatorAddress": "io1qnec80ark9shjc6uzk45dhm8s50dpc27sjuver"
      },
      "alias": {
        "exist": true,
        "aliasName": "pubxpayments"
      },
      "totalNumberOfHolders": 9006,
      "totalAccountSupply": "782833468919740605141266758"
    }
  }
}

```

## Action

### ByDates

```text
Usage:
  ByDates finds actions by dates

Request:
  startDate: start date in unix epoch time
  endDate: end date in unix epoch time
  pagination:
    skip: starting index of displaying action list
    first: number of actions to display

Response:
  exist: whether actions exist within the time frame
  actions:
    actHash: action hash
    blkHash: block hash
    timeStamp: timestamp
    actType: action type
    sender: sender address
    recipient: recipient address
    amount: amount transferred
    gasFee: gas fee
  count: total number of actions within the time frame

```

### ByHash

```text
Usage:
  ByHash finds the action by hash

Request:
  actHash: action hash

Response:
  actionInfo:
    actHash: action hash
    blkHash: block hash
    timeStamp: timestamp
    actType: action type
    sender: sender address
    recipient: recipient address
    amount: amount transferred
    gasFee: gas fee
  evmTransfers:
    from: sender address
    to: recipient address
    quantity: amount transferred
```

### ByAddress

```text
Usage:
  ByAddress finds actions by address

Request:
  address: sender address or recipient address
  pagination:
    skip: starting index of displaying action list
    first: number of actions to display

Response:
  exist: whether actions exist for the given address
  actions:
    actHash: action hash
    blkHash: block hash
    timeStamp: timestamp
    actType: action type
    sender: sender address
    recipient: recipient address
    amount: amount transferred
    gasFee: gas fee
  count: total number of actions for the given address

```

### EvmTransfersByAddress

```text
Usage:
  EvmTransfersByAddress finds EVM transfers by address

Request:
  address: sender address or recipient address
  pagination:
    skip: starting index of displaying action list
    first: number of actions to display

Response:
  exist: whether EVM transfers exist for the given address
  evmTransfers:
    from: sender address
    to: recipient address
    quantity: amount transferred
    actHash: action hash
    blkHash: block hash
    timeStamp: timestamp
  count: total number of EVM transfers for the given address

```

### ByType

```text
Usage:
  ByType finds actions by action type

Request:
  type: action type
  pagination:
    skip: starting index of displaying action list
    first: number of actions to display

Response:
  exist: whether actions exist for the given type
  actions:
    actHash: action hash
    blkHash: block hash
    timeStamp: timestamp
    actType: action type
    sender: sender address
    recipient: recipient address
    amount: amount transferred
    gasFee: gas fee
  count: total number of actions for the given type
```

Demo:

```text
Sample Request:

query{
  action{
    byDates(startDate: 1589485984, endDate: 1589486028) {
      exist
      actions(pagination: {skip: 0, first: 1}){
        actHash
        blkHash
        timeStamp
        actType
        sender
        recipient
        amount
        gasFee
      }
      count
    }
    byHash(actHash: "000086e6e3034c104025896f8af9d3e313b95957c076b3a5ebe1f42f8af3a8ad"){
      actionInfo{
        actHash
    		blkHash
    		timeStamp
    		actType
    		sender
    		recipient
    		amount
    		gasFee
      }
      evmTransfers{
        from
        to
        quantity
      }
    }
    byAddress(address:"io17jz7vtvllrgctkrvzmmue55feuk8cy6mtcynkk"){
      exist
      actions(pagination: {skip: 0, first: 1}){
        actHash
        blkHash
        timeStamp
        actType
        sender
        recipient
        amount
        gasFee
      }
      count
    }
    evmTransfersByAddress(address: "io1nkuv5ns3pevh7r7cwv6lwa2744utyhq7txay3a"){
      exist
  		evmTransfers{
        from
        to
        quantity
        actHash
        blkHash
        timeStamp
      }
    	count
    }
    byType(type:"transfer"){
      exist
      actions(pagination: {skip: 0, first: 1}){
        actHash
        blkHash
        timeStamp
        actType
        sender
        recipient
        amount
        gasFee
      }
      count
    }
  }
}

Sample Response:

{
  "data": {
    "action": {
      "byDates": {
        "exist": true,
        "actions": [
          {
            "actHash": "8c917d11bff3856d60d274c666188afc3aac0fbcddb60bd19cf9a352cb7b00a3",
            "blkHash": "293845611de09b944c5def5a6b29e83cd4b8d2a00a29575e4720fc64e8adf7b4",
            "timeStamp": 1589486025,
            "actType": "grantReward",
            "sender": "io195mh6ftwz5vnagw984fj4hj8awty3ue2gh457f",
            "recipient": "",
            "amount": "0",
            "gasFee": "0"
          }
        ],
        "count": 9
      },
      "byHash": {
        "actionInfo": {
          "actHash": "000086e6e3034c104025896f8af9d3e313b95957c076b3a5ebe1f42f8af3a8ad",
          "blkHash": "2f31b5b15c50dc9431cd1f655fdace2c2c7bf92111a4a01a9947ce3969352d00",
          "timeStamp": 1582409835,
          "actType": "transfer",
          "sender": "io1ey8s7p7kzu9lh68we7mstmyllaxc6tgwuj2whh",
          "recipient": "io1nkuv5ns3pevh7r7cwv6lwa2744utyhq7txay3a",
          "amount": "1528012374156719350",
          "gasFee": "10000000000000000"
        },
        "evmTransfers": []
      },
      "byAddress": {
        "exist": true,
        "actions": [
          {
            "actHash": "e1e3d46844046710d4843b2b044f8ff5da785931e808ac071ff4b4280a05aa9e",
            "blkHash": "3b1dcebd95f35a682ea8f443ae817b240b447e50a23c3a60918c3318bb249ccc",
            "timeStamp": 1589442290,
            "actType": "execution",
            "sender": "io17jz7vtvllrgctkrvzmmue55feuk8cy6mtcynkk",
            "recipient": "io1hp6y4eqr90j7tmul4w2wa8pm7wx462hq0mg4tw",
            "amount": "0",
            "gasFee": "60357000000000000"
          }
        ],
        "count": 290
      },
      "evmTransfersByAddress": {
        "exist": true,
        "evmTransfers": [
          {
            "from": "io1zn9mn4v63jg3047ylqx9nqaqz0ev659777q3xc",
            "to": "io1nkuv5ns3pevh7r7cwv6lwa2744utyhq7txay3a",
            "quantity": "5006000000000000000000",
            "actHash": "8f4c40742081668eaab315701f5603dc83ecc455cacffb3b13710c37915cb4dc",
            "blkHash": "3625674",
            "timeStamp": 1583322240
          },
          {
            "from": "io1nkuv5ns3pevh7r7cwv6lwa2744utyhq7txay3a",
            "to": "io1zn9mn4v63jg3047ylqx9nqaqz0ev659777q3xc",
            "quantity": "0",
            "actHash": "8f4c40742081668eaab315701f5603dc83ecc455cacffb3b13710c37915cb4dc",
            "blkHash": "3625674",
            "timeStamp": 1583322240
          },
          {
            "from": "io1nkuv5ns3pevh7r7cwv6lwa2744utyhq7txay3a",
            "to": "io1hp6y4eqr90j7tmul4w2wa8pm7wx462hq0mg4tw",
            "quantity": "0",
            "actHash": "c4bd25240b0d8832b0dca2916d30e3c6882a5dbfa803573950ad8ae894ef8f5c",
            "blkHash": "3572472",
            "timeStamp": 1583055260
          },
          {
            "from": "io1nkuv5ns3pevh7r7cwv6lwa2744utyhq7txay3a",
            "to": "io1zn9mn4v63jg3047ylqx9nqaqz0ev659777q3xc",
            "quantity": "0",
            "actHash": "078c9d6c2f18681d9d3747d967919a7fafb44598a39117b9a1a1abc8e18e6013",
            "blkHash": "3572471",
            "timeStamp": 1583055255
          },
          {
            "from": "io1nkuv5ns3pevh7r7cwv6lwa2744utyhq7txay3a",
            "to": "io1zn9mn4v63jg3047ylqx9nqaqz0ev659777q3xc",
            "quantity": "5006000000000000000000",
            "actHash": "fee1360940bb6724636c0731edde984a62941df2e1785361749a50bee6f22559",
            "blkHash": "3316376",
            "timeStamp": 1581770210
          }
        ],
        "count": 5
      },
      "byType": {
        "exist": true,
        "actions": [
          {
            "actHash": "000086e6e3034c104025896f8af9d3e313b95957c076b3a5ebe1f42f8af3a8ad",
            "blkHash": "2f31b5b15c50dc9431cd1f655fdace2c2c7bf92111a4a01a9947ce3969352d00",
            "timeStamp": 1582409835,
            "actType": "transfer",
            "sender": "io1ey8s7p7kzu9lh68we7mstmyllaxc6tgwuj2whh",
            "recipient": "io1nkuv5ns3pevh7r7cwv6lwa2744utyhq7txay3a",
            "amount": "1528012374156719350",
            "gasFee": "10000000000000000"
          }
        ],
        "count": 132221
      }
    }
  }
}
```

## XRC20 Tokens

### ByContractAddress

```text
Usage:
  ByContractAddress returns Xrc20 actions given the Xrc20 contract address

Request:
  address: contract address
  numberPerPage: number per page
  page: page number

Response:
  exist: whether Xrc20 actions exist for the given contract address
  xrc20:
    contract: contract address
    hash: action hash
    timestamp: timestamp
    from: sender address
    to: recipient address
    quantity: amount transferred
  count: total number of Xrc20 actions
```

### ByAddress

```text
Usage:
  ByAddress returns Xrc20 actions given the sender address or recipient address

Request:
  address: sender address or recipient address
  numberPerPage: number per page
  page: page number

Response:
  exist: whether Xrc20 actions exist for the given sender address or recipient address
  xrc20:
    contract: contract address
    hash: action hash
    timestamp: timestamp
    from: sender address
    to: recipient address
    quantity: amount transferred
  count: total number of Xrc20 actions
```

### ByPage

```text
Usage:
  ByPage returns Xrc20 actions by pagination

Request:
  pagination:
    skip: starting index of displaying action list
    first: number of actions to display

Response:
  exist: whether Xrc20 actions exist
  xrc20:
    contract: contract address
    hash: action hash
    timestamp: timestamp
    from: sender address
    to: recipient address
    quantity: amount transferred
  count: total number of Xrc20 actions
```

### Xrc20Addresses

```text
Usage:
  Xrc20Addresses returns Xrc20 contract addresses

Request:
  pagination:
    skip: starting index of displaying contract address list
    first: number of contract addresses to display

Response:
  exist: whether Xrc20 contract addresses exist
  addresses: contract address list
  count: total number of Xrc20 contract addresses

```

### TokenHolderAddresses

```text
Usage:
  TokenHolderAddresses returns Xrc20 token holder addresses given a Xrc20 contract address

Request:
  tokenAddress: token contract address
  pagination:
    skip: starting index of displaying token holder address list
    first: number of token holder addresses to display

Response:
  addresses: token holder address list
  count: total number of token holder addresses
```

Demo:

```text
Sample Request:
query{
  xrc20{
    byContractAddress(address: "io1hp6y4eqr90j7tmul4w2wa8pm7wx462hq0mg4tw", page: 1, numPerPage: 1){
      exist
      xrc20 {
        contract
        hash
        timestamp
        from
        to
        quantity
      }
      count
    }
    byAddress(address: "io1l6a6gu9ks4pwu2tmrzhl6z2el73ydv6e768p5x", page: 1, numPerPage: 1){
      exist
      xrc20 {
        contract
        hash
        timestamp
        from
        to
        quantity
      }
      count
    }
    byPage(pagination: {skip: 0, first: 2}){
      exist
      xrc20 {
        contract
        hash
        timestamp
        from
        to
        quantity
      }
      count
    }
    xrc20Addresses(pagination:{skip: 0, first: 2}){
      exist
      addresses
      count
    }
    tokenHolderAddresses(tokenAddress: "io1hp6y4eqr90j7tmul4w2wa8pm7wx462hq0mg4tw"){
      addresses(pagination: {skip: 1, first: 2})
      count
    }
  }
}

Sample Response:

{
  "data": {
    "xrc20": {
      "byContractAddress": {
        "exist": true,
        "xrc20": [
          {
            "contract": "io1hp6y4eqr90j7tmul4w2wa8pm7wx462hq0mg4tw",
            "hash": "052eebdc0bc75715ffedeb34c9322446230448747cef48762be9478fd8a7064e",
            "timestamp": "1589496125",
            "from": "io1qqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqd39ym7",
            "to": "io1xrwjjy26e5dmcxd2dq6hu0zsfrd5qdgqpg57m8",
            "quantity": "71735598998424445289"
          }
        ],
        "count": 80440
      },
      "byAddress": {
        "exist": true,
        "xrc20": [
          {
            "contract": "io1hp6y4eqr90j7tmul4w2wa8pm7wx462hq0mg4tw",
            "hash": "df8c34d9bcee1ed204ba82ebcf5b29722956379ef734c1e1e32fcb6a98968b5d",
            "timestamp": "1589480485",
            "from": "io1qqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqd39ym7",
            "to": "io1l6a6gu9ks4pwu2tmrzhl6z2el73ydv6e768p5x",
            "quantity": "1031249148674903495207"
          }
        ],
        "count": 235
      },
      "byPage": {
        "exist": true,
        "xrc20": [
          {
            "contract": "io1hp6y4eqr90j7tmul4w2wa8pm7wx462hq0mg4tw",
            "hash": "052eebdc0bc75715ffedeb34c9322446230448747cef48762be9478fd8a7064e",
            "timestamp": "1589496125",
            "from": "io1qqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqd39ym7",
            "to": "io1xrwjjy26e5dmcxd2dq6hu0zsfrd5qdgqpg57m8",
            "quantity": "71735598998424445289"
          },
          {
            "contract": "io1hp6y4eqr90j7tmul4w2wa8pm7wx462hq0mg4tw",
            "hash": "f8a326ddb67c0140be0244a052976d73ca6f8fcb5278c51549df80c347c7a3b6",
            "timestamp": "1589496065",
            "from": "io1qqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqd39ym7",
            "to": "io1qnwl44fpln3uvxrrhjxkp56y6n3j6cqctp76rq",
            "quantity": "132716426277978885524"
          }
        ],
        "count": 86196
      },
      "xrc20Addresses": {
        "exist": true,
        "addresses": [
          "io1hp6y4eqr90j7tmul4w2wa8pm7wx462hq0mg4tw",
          "io1lvemm43lz6np0hzcqlpk0kpxxww623z5hs4mwu"
        ],
        "count": 3
      },
      "tokenHolderAddresses": {
        "addresses": [
          "io1quwq28fk0z6ztyesw8r8aalpww62uf7m6xjf8x",
          "io1hn57s343wgqrvqkt0mp4fas0wfvgtwecny5lq5"
        ],
        "count": 1871
      }
    }
  }
}
```

## XRC721 Tokens

### ByContractAddress

```text
Usage:
  ByContractAddress returns Xrc721 actions given the Xrc721 contract address

Request:
  address: contract address
  numberPerPage: number per page
  page: page number

Response:
  exist: whether Xrc721 actions exist for the given contract address
  xrc721:
    contract: contract address
    hash: action hash
    timestamp: timestamp
    from: sender address
    to: recipient address
    quantity: amount transferred
  count: total number of Xrc721 actions

```

### ByAddress

```text
Usage:
  ByAddress returns Xrc721 actions given the sender address or recipient address

Request:
  address: sender address or recipient address
  numberPerPage: number per page
  page: page number

Response:
  exist: whether Xrc721 actions exist for the given sender address or recipient address
  xrc721:
    contract: contract address
    hash: action hash
    timestamp: timestamp
    from: sender address
    to: recipient address
    quantity: amount transferred
  count: total number of Xrc721 actions

```

### ByPage

```text
Usage:
  ByPage returns Xrc721 actions by pagination

Request:
  pagination:
    skip: starting index of displaying action list
    first: number of actions to display

Response:
  exist: whether Xrc721 actions exist
  xrc721:
    contract: contract address
    hash: action hash
    timestamp: timestamp
    from: sender address
    to: recipient address
    quantity: amount transferred
  count: total number of Xrc721 actions
```

### Xrc721Addresses

```text
Usage:
  Xrc721Addresses returns Xrc721 contract addresses

Request:
  pagination:
    skip: starting index of displaying contract address list
    first: number of contract addresses to display

Response:
  exist: whether Xrc721 contract addresses exist
  addresses: contract address list
  count: total number of Xrc721 contract addresses

```

### TokenHolderAddresses

```text
Usage:
  TokenHolderAddresses returns Xrc721 token holder addresses given a Xrc721 contract address

Request:
  tokenAddress: token contract address
  pagination:
    skip: starting index of displaying token holder address list
    first: number of token holder addresses to display

Response:
  addresses: token holder address list
  count: total number of token holder addresses
```

{% hint style="warning" %}
**TODO**: When there are Xrc721 actions on the chain, add a demo here.
{% endhint %}

### TopHolders <a id="topholders"></a>

```text
Usage:
  TopHolders returns the top IOTX holders

Request:
  endEpochNumber: end epoch number
  pagination:
    skip: starting index of displaying top holder list
    first: number of top holders to display

Response:
  address: holder address
  balance: account balance
```

Demo:

```text
Sample Request:

query{
  topHolders(endEpochNumber: 1000, pagination: {skip: 0, first: 5}){
    address
    balance
  }
}

Sample Response:

{
  "data": {
    "topHolders": [
      {
        "address": "io1uqhmnttmv0pg8prugxxn7d8ex9angrvfjfthxa",
        "balance": "9782327287860000000000000000"
      },
      {
        "address": "io1v8aj79xc7zdn46rptrqe63g79tgq57s8em2yk5",
        "balance": "5595872065018750000000000"
      },
      {
        "address": "io1w2zkwsda29cryeg8rtln6wl0nm2mrlfl2xj02c",
        "balance": "5000000000000000000000000"
      },
      {
        "address": "io17zjv5f97j0d9fp6svqnvf2nf3k4a5pjay9kzp9",
        "balance": "3457911717681240000000000"
      },
      {
        "address": "io183v7vftj3e4h76z5f5qpswhnn5737rrwjkhyds",
        "balance": "1222486212327000000000000"
      }
    ]
  }
}
```

  


## Hermes

```text
Usage:
  Hermes gives delegates who register the service of automatic reward distribution an overview of the reward distributions to their voters within a range of epochs

Request:
  startEpoch: starting epoch number
  epochCount: epoch count
  rewardAddress: Hermes reward address
  waiverThreshold: threshold for waiving service fee

Response:
  exist: whether Hermes has bookkeeping information within the specified epoch range
  hermesDistribution:
    delegateName: delegate name
    rewardDistribution:
      voterEthAddress: voter’s ERC20 address
      voterIotexAddress: voter’s IoTeX address
      amount: amount of reward distribution
    stakingIotexAddress: delegate IoTeX staking address
    voterCount: number of voters
    waiveServiceFee: whether the delegate is qualified for waiving the service fee
    refund: amount of refund
```

Demo:

```text
Sample Request:

query{
  hermes(startEpoch: 2600, epochCount: 2, rewardAddress: "io12mgttmfa2ffn9uqvn0yn37f4nz43d248l2ga85", waiverThreshold: 100) {
    exist
    hermesDistribution{
      delegateName
      rewardDistribution{
        voterEthAddress
        voterIotexAddress
        amount
      }
      stakingIotexAddress
      waiveServiceFee
      refund
    }
  }
}

Sample Reponse:

{
  "data": {
    "hermes": {
      "exist": true,
      "hermesDistribution": [
        {
          "delegateName": "coredev",
          "rewardDistribution": [
            {
              "voterEthAddress": "0x2ed3767cfcbceb42ff5f3642d4df6f851b947073",
              "voterIotexAddress": "io19mfhvl8uhn459l6lxepdfhm0s5degurn9p9ws7",
              "amount": "196604399213276651"
            },
            {
              "voterEthAddress": "0xd24687dc4512cd705a74cd5495745398f24278ad",
              "voterIotexAddress": "io16frg0hz9ztxhqkn5e42f2aznnreyy79dmqlsn2",
              "amount": "32631320141532384677"
            },
            {
              "voterEthAddress": "0xfe7bcb3676aabe9a6b39cb23f3a5fa41eed7ad1b",
              "voterIotexAddress": "io1leaukdnk42lf56eeev3l8f06g8hd0tgmep8z96",
              "amount": "359747231878966643458"
            }
          ],
          "stakingIotexAddress": "io16frg0hz9ztxhqkn5e42f2aznnreyy79dmqlsn2",
          "waiveServiceFee": false,
          "refund": "20661850337879594993"
        }
      ]
    }
  }
}
```

### HermesAverageStats

```text
Usage:
  HermesAverageStats returns the Hermes average statistics

Request:
  startEpoch: starting epoch number
  epochCount: epoch count
  rewardAddress: Hermes reward address

Response:
  exist: whether Hermes has bookkeeping information within the specified epoch range
  averagePerEpoch:
    delegateName: delegate name
    rewardDistribution: reward distribution amount on average
    totalWeightedVotes: total weighted votes on average
```

Demo:

```text
Sample Request:

query{
  hermesAverageStats(startEpoch: 5000, epochCount: 10, rewardAddress: "io12mgttmfa2ffn9uqvn0yn37f4nz43d248l2ga85"){
    exist
    averagePerEpoch{
      delegateName
      rewardDistribution
      totalWeightedVotes
    }
  }
}

Sample Response:
{
  "data": {
    "hermesAverageStats": {
      "exist": true,
      "averagePerEpoch": [
        {
          "delegateName": "coredev",
          "rewardDistribution": "401032105356051868726",
          "totalWeightedVotes": "38808174674986270729016008"
        },
        {
          "delegateName": "droute",
          "rewardDistribution": "822447995100870198028",
          "totalWeightedVotes": "118158036851736955093703620"
        },
        {
          "delegateName": "enlightiv",
          "rewardDistribution": "307702229045005783993",
          "totalWeightedVotes": "44203263243950087278116762"
        },
        {
          "delegateName": "gamefantasy#",
          "rewardDistribution": "615239097651479380485",
          "totalWeightedVotes": "57767718207147312170110160"
        },
        {
          "delegateName": "hashquark",
          "rewardDistribution": "541329441223848778034",
          "totalWeightedVotes": "37303750004462544031788788"
        },
        {
          "delegateName": "hotbit",
          "rewardDistribution": "490966398085098750279",
          "totalWeightedVotes": "41618068480725476480096115"
        },
        {
          "delegateName": "huobiwallet",
          "rewardDistribution": "256863403704895657860",
          "totalWeightedVotes": "36902607956443015195845625"
        },
        {
          "delegateName": "thebottoken#",
          "rewardDistribution": "76273140665872145706",
          "totalWeightedVotes": "10349106879165645178941803"
        }
      ]
    }
  }
}
```

## Hermes2

### ByDelegate

```text
Usage:
  ByDelegate returns Hermes delegates' distribution history

Request:
  startEpoch: starting epoch number
  epochCount: epoch count
  delegateName: delegate name
  pagination:
    skip: starting index of displaying reward distribution list
    first: number of reward distributions to display

Response:
  exist: whether the delegate uses Hermes within the specified epoch range
  voterInfoList:
    voterAddress: voter address
    fromEpoch: starting epoch of bookkeeping
    toEpoch: ending epoch of bookkeeping
    amount: distributino amount
    actionHash: action hash
    timestamp: timestamp
  count: total number of reward distributions
  totalRewardDistributed: total reward amount distributed
  distributionRatio:
    epochNumber: epoch number
    blockRewardRatio: ratio of block reward being distributed
    epochRewardRatio: ratio of epoch reward being distributed
    foundationBonusRatio: ratio of foundation bonus being distributed
```

### ByVoter

```text
Usage:
  ByVoter returns Hermes voters' receiving history

Request:
  startEpoch: starting epoch number
  epochCount: epoch count
  voterAddress: voter address
  pagination:
    skip: starting index of displaying reward receiving list
    first: number of reward receivings to display

Response:
  exist: whether the voter uses Hermes within the specified epoch range
  delegateInfoList:
    delegateName: delegate name
    fromEpoch: starting epoch of bookkeeping
    toEpoch: ending epoch of bookkeeping
    amount: receiving amount
    actionHash: action hash
    timestamp: timestamp
  count: total number of reward receivings
  totalRewardReceived: total reward amount received
```

### HermesMeta

```text
Usage:
  HermesMeta provides Hermes platform metadata

Request:
  startEpoch: starting epoch number
  epochCount: epoch count

Response:
  exist: whether Hermes has bookkeeping information within the specified epoch range
  numberOfDelegates: number of Hermes delegates within the epoch range
  numberOfRecipients: number of voters who vote for Hermes delegates within the epoch range
  totalRewardDistributed: total reward amount distributed within the epoch range

```

Demo:

```text
Sample Request:

query{
  hermes2(startEpoch: 9100, epochCount: 1){
    byDelegate(delegateName:"gamefantasy#"){
      exist
      voterInfoList(pagination: {skip: 0, first: 2}){
        voterAddress
        fromEpoch
        toEpoch
        amount
        actionHash
        timestamp
      }
      count
      totalRewardsDistributed
      distributionRatio{
        epochNumber
        blockRewardRatio
        epochRewardRatio
        foundationBonusRatio
      }
    }
    byVoter(voterAddress: "io19jgwy6gua2mxtthdgqe7r6v2z8jyvv0820nshw"){
      exist
      delegateInfoList(pagination: {skip: 0, first: 2}){
        delegateName
        fromEpoch
        toEpoch
        amount
        actionHash
        timestamp
      }
      count
      totalRewardsReceived
    }
    hermesMeta{
      exist
      numberOfDelegates
      numberOfRecipients
      totalRewardsDistributed
    }
  }
}

Sample Response:

{
  "data": {
    "hermes2": {
      "byDelegate": {
        "exist": true,
        "voterInfoList": [
          {
            "voterAddress": "io1qhks2tct2386xgntkgg8f748ymuqnzwy4qr3ms",
            "fromEpoch": 9016,
            "toEpoch": 9037,
            "amount": "898496142232422125",
            "actionHash": "bff5c21cec38a994507cc133220d853710516b931a44d0ee74816fe835d68b62",
            "timestamp": "2020-05-08 00:10:45 +0000 UTC"
          },
          {
            "voterAddress": "io1qk59a7q45spm8c2tnuf2j3yrkshfupaeq6fa8g",
            "fromEpoch": 9016,
            "toEpoch": 9037,
            "amount": "4597907624862488628",
            "actionHash": "bff5c21cec38a994507cc133220d853710516b931a44d0ee74816fe835d68b62",
            "timestamp": "2020-05-08 00:10:45 +0000 UTC"
          }
        ],
        "count": 79,
        "totalRewardsDistributed": "15856874829304723790254",
        "distributionRatio": [
          {
            "epochNumber": 9100,
            "blockRewardRatio": 80,
            "epochRewardRatio": 80,
            "foundationBonusRatio": 80
          }
        ]
      },
      "byVoter": {
        "exist": true,
        "delegateInfoList": [
          {
            "delegateName": "thebottoken#",
            "fromEpoch": 9016,
            "toEpoch": 9037,
            "amount": "758460957121496239828",
            "actionHash": "e6a8a1a3daa35bfec01537aecc45fd5d9f58d4fd686e152e6a44c6c5e6c7cc25",
            "timestamp": "2020-05-08 00:23:45 +0000 UTC"
          },
          {
            "delegateName": "consensusnet",
            "fromEpoch": 9016,
            "toEpoch": 9037,
            "amount": "2281108960667527338399",
            "actionHash": "ada939af05ba7bf96d4e87a2c5f7d048f48ab9b6fafc3ee1ca35dfc67664a22a",
            "timestamp": "2020-05-08 00:02:40 +0000 UTC"
          }
        ],
        "count": 3,
        "totalRewardsReceived": "5315407956761306754362"
      },
      "hermesMeta": {
        "exist": true,
        "numberOfDelegates": 22,
        "numberOfRecipients": 964,
        "totalRewardsDistributed": "241471851581857403438503"
      }
    }
  }
}
```

