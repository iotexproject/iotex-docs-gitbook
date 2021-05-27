# Query the Blockchain

## Query the Blockchain

`Usage: ioctl bc info`

```javascript
➜  ioctl bc info
Blockchain Node: api.iotex.one:443
{
  "height": 11283255,
  "numActions": 14393325,
  "tps": 1,
  "epoch": {
    "num": 18194,
    "height": 11282761
  },
  "tpsFloat": 0.29090908
}
```

### Query Block <a id="query-block"></a>

`Usage: ioctl bc block [HEIGHT|HASH]`

```javascript
➜  ioctl bc block
Blockchain Node: api.iotex.one:443
{
  "hash": "b73d48301aa75ab2f6c6e3350abb4b050852eebd89a333f9b2f412c9011f37ba",
  "height": 11283260,
  "timestamp": {
    "seconds": 1621955365
  },
  "numActions": 1,
  "producerAddress": "io1ddjluttkzljqfgdtcz9eu3r3s832umy7ylx0ts",
  "transferAmount": "0",
  "txRoot": "d401ba17a772340f6aa0284357fa65758c9063c755c25721cab86e3b674e096b",
  "receiptRoot": "8205af86ab185619edf8cb2279774bf5c3b322fb1ad7855719f8f29ac50734a4",
  "deltaStateDigest": "835b130e5fe7333da7287b4a61011bf575cfef2386c58e2eedf8c100007aeed0",
  "logsBloom": "00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
  "previousBlockHash": "ec1d8f515ffc90cc2c549b6d9ae0ff07d6d9681137f4fe40d78e9d8f10228d8d"
}
```

```javascript
➜  ioctl bc block 101
Blockchain Node: api.iotex.one:443
{
  "hash": "1930df275ea54c87fcdd3909e0382c26fc14aa970433e6a6302eb393c829634e",
  "height": 101,
  "timestamp": {
    "seconds": 1555899830
  },
  "numActions": 1,
  "producerAddress": "io1vtm2zgn830pn6auc2cvnchgwdaefa9gr4z0s86",
  "transferAmount": "0",
  "txRoot": "5a94b4defdc18cf84e6515f9c125052cc1aedf27c6be2a378acd34a47ab2a286",
  "receiptRoot": "3066ce28bd35faf02e98d2821eb2aa94fff31cca71f93675fea4a58f0963ab66",
  "deltaStateDigest": "a9f953c5b5e71a2dba36e3caa7b2aeb6c1722f5d8d2bbbe08e9af849e40adc40",
  "previousBlockHash": "ac661375315b444ad4feff5e96db11eb01d55af2a850f5504180c8bf8a4d39f4"
}

```

```javascript
➜  ioctl bc block 1930df275ea54c87fcdd3909e0382c26fc14aa970433e6a6302eb393c829634e                                      1 ↵
Blockchain Node: api.iotex.one:443
{
  "hash": "1930df275ea54c87fcdd3909e0382c26fc14aa970433e6a6302eb393c829634e",
  "height": 101,
  "timestamp": {
    "seconds": 1555899830
  },
  "numActions": 1,
  "producerAddress": "io1vtm2zgn830pn6auc2cvnchgwdaefa9gr4z0s86",
  "transferAmount": "0",
  "txRoot": "5a94b4defdc18cf84e6515f9c125052cc1aedf27c6be2a378acd34a47ab2a286",
  "receiptRoot": "3066ce28bd35faf02e98d2821eb2aa94fff31cca71f93675fea4a58f0963ab66",
  "deltaStateDigest": "a9f953c5b5e71a2dba36e3caa7b2aeb6c1722f5d8d2bbbe08e9af849e40adc40",
  "previousBlockHash": "ac661375315b444ad4feff5e96db11eb01d55af2a850f5504180c8bf8a4d39f4"
}
```

### Query Staking Bucket Information

`Usage: ioctl bc bucketlist [ALIAS|ADDRESS]`

```javascript
➜  ioctl bc bucketlist daddypig
Blockchain Node: api.testnet.iotex.one:443
{
    index: 56
    owner: io1gh439pm67d4cwxt882xpylj75klys6esepml60
    candidate: io1q2whygmmzphr22fh5703l04jz5kh9thj9dgs99
    stakedAmount: 232 IOTX
    stakedDuration: 7 days
    autoStake: false
    createTime: 2020-05-21T13:10:10Z
    stakeStartTime: 2020-05-21T13:28:25Z
    unstakeStartTime: none
}
```

### Query Buckets By Candidate

`Usage: ioctl bc bucketlist cand [CANDIDATE_NAME] [OFFSET] [LIMIT]`

```javascript
➜  ioctl bc bucketlist cand longz 0 10
Blockchain Node: api.testnet.iotex.one:443
{
    index: 34
    owner: io120au9ra0nffdle04jx2g5gccn6gq8qd4fy03l4
    candidate: io1t56twy23yjuqscljpjc869hyqw3gpswwj0g228
    stakedAmount: 100 IOTX
    stakedDuration: 7 days
    autoStake: false
    createTime: 2020-05-11T06:41:20Z
    stakeStartTime: 2020-05-11T06:41:20Z
    unstakeStartTime: none
}
{
    index: 43
    owner: io120au9ra0nffdle04jx2g5gccn6gq8qd4fy03l4
    candidate: io1l40dc4q95fsjdprhcga5qrpdsj46q3wpzr27n9
    stakedAmount: 170 IOTX
    stakedDuration: 14 days
    autoStake: false
    createTime: 2020-05-14T02:42:15Z
    stakeStartTime: 2020-05-14T02:42:15Z
    unstakeStartTime: none
}
```

### Query Buckets By Voter

`Usage: ioctl bc bucketlist voter [VOTER_ADDRESS] [OFFSET] [LIMIT]`

```javascript
➜  ioctl bc bucketlist voter tmp2 0 10
Blockchain Node: api.testnet.iotex.one:443
{
    index: 34
    owner: io120au9ra0nffdle04jx2g5gccn6gq8qd4fy03l4
    candidate: io1t56twy23yjuqscljpjc869hyqw3gpswwj0g228
    stakedAmount: 100 IOTX
    stakedDuration: 7 days
    autoStake: false
    createTime: 2020-05-11T06:41:20Z
    stakeStartTime: 2020-05-11T06:41:20Z
    unstakeStartTime: none
}
{
    index: 43
    owner: io120au9ra0nffdle04jx2g5gccn6gq8qd4fy03l4
    candidate: io1l40dc4q95fsjdprhcga5qrpdsj46q3wpzr27n9
    stakedAmount: 170 IOTX
    stakedDuration: 14 days
    autoStake: false
    createTime: 2020-05-14T02:42:15Z
    stakeStartTime: 2020-05-14T02:42:15Z
    unstakeStartTime: none
}
```

### Query Bucket By Index

`Usage: ioctl bc bucket [BUCKET_INDEX]`

```javascript
➜  ioctl bc bucket 56
Blockchain Node: api.testnet.iotex.one:443
{
	index: 56
	owner: io19n5sqmreq4tk7w7xevnwms9ux8h7kuemjrjlf7
	candidate: io1xrcfzdmujtr9hvmrm58yxvhe5djahdzt30ljs2
	stakedAmount: 100 IOTX
	stakedDuration: 0 days
	autoStake: false
	createTime: 2020-06-01T18:32:35Z
	stakeStartTime: 2020-06-01T18:32:35Z
	unstakeStartTime: none
}

```

### Query Delegates <a id="query-delegates-2"></a>

`Usage: ioctl node delegate [-e epoch-num]`

```javascript
➜  ioctl node delegate
Epoch: 18194,  Start block height: 11282761,Total blocks produced in epoch: 542

Address                                     Name           Rank   Alias   Status   Blocks   ProbatedStatus    Votes
io1jzteq7gc5sh8tfp5auz8wwj97kvdapr9y8wzne   binancevote       1                    0                        414565318.738108275911974163
io10reczcaelglh5xmkay65h9vw3e5dp82e8vw0rz   metanyx           2                    0                        209094580.94368987269441618
io189zlpedmhs3cg4zhyle2u8f9shkztwd3n3d7zd   satoshimusk       3           active   22                       141597515.304090309742324742
io1tfke5nfwryte6nultpmqefadgm0dsahm2gm63k   iotexlab          4                    0                        104597977.604617043282262392
...                                         ...              ..              ...   ..                            ... 
io1u4pev9u5as7ujpk29wpsrc95m8kuhec3pmuk72   hashquark        35           active   23                       46788920.335452899578834654
io1l42qgv8328h8x7pde35w3szh59elhw8nwmcy6j   cryptozoo        36           active   22                       45750281.527141635145186376

```

```javascript
➜  ioctl node delegate -e 18193
Epoch: 18193,  Start block height: 11282041,Total blocks produced in epoch: 720

Address                                     Name           Rank   Alias   Status   Blocks   ProbatedStatus    Votes
io1jzteq7gc5sh8tfp5auz8wwj97kvdapr9y8wzne   binancevote       1                    0                        414564878.655601430673104648
io10reczcaelglh5xmkay65h9vw3e5dp82e8vw0rz   metanyx           2                    0                        209217627.214848890340299665
io189zlpedmhs3cg4zhyle2u8f9shkztwd3n3d7zd   satoshimusk       3           active   30                       141597514.574782833722376484
io1tfke5nfwryte6nultpmqefadgm0dsahm2gm63k   iotexlab          4           active   30                       104544157.060103748426275375
...                                         ...              ..              ...   ..                            ... 
io1l42qgv8328h8x7pde35w3szh59elhw8nwmcy6j   cryptozoo        35           active   30                       45750281.495953941578199214
io1u4pev9u5as7ujpk29wpsrc95m8kuhec3pmuk72   hashquark        36                    0                        45337106.848622283990092254

```

### Query Probation List <a id="query-probation-list"></a>

`Usage: ioctl node probationlist [-e epoch-num]`

```javascript
➜  ioctl node probationlist
EpochNumber : 4985, IntensityRate : 90%
ProbationList : [
  "io1gh439pm67d4cwxt882xpylj75klys6esepml60"
]

```

```javascript
➜  ioctl node probationlist -e 4500
EpochNumber : 4500, IntensityRate : 90%
ProbationList : [
  "io13n3382cjhaawmqfk4vmvvgllnryw4tf56qdtks",
  "io1gh439pm67d4cwxt882xpylj75klys6esepml60"
]
```

### Query Reward <a id="query-reward"></a>

`Usage: ioctl node reward unclaimed|pool [ALIAS|DELEGATE_ADDRESS]`

```javascript
➜  ioctl node reward unclaimed whale
io1t54nfdnpldaxkpm35f2gzh3rx6cakypmp5xfz5: 45819 IOTX
```

```javascript
➜  ioctl node reward pool
Total Unclaimed:	 26567469.425867808134990226 IOTX
Total Available:	 720630085.427229243274397982 IOTX
Total Balance:		 747197554.853097051409388208 IOTX
```

