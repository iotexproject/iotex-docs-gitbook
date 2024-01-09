# Accounts

### Create

`Usage: ioctl account create`

```javascript
➜  ioctl account create
{
  "accounts": [
    {
      "address": "io12ly97a3sk94ne06qjz2vv6clv3za7mk2z2sra9",
      "privateKey": "bb59a2a2c21242831906e0c8d188c642fdc1324d27ac4ae0d8cbea373b22147b",
      "publicKey": "040780ba149d24ee5418084ee193a6be8b3b7cf5329d160fc8902270b342c4fed4b646cdd5fdaf52932eecb957297a9bf6dbb24f7faa9287a27df6b5e83781c74b"
    }
  ]
}
```

```javascript
➜  ioctl account create -n 3
{
  "accounts": [
    {
      "address": "io1dcx2490vk2sg0f7ujv9d3gu67rpvyk5rjp854s",
      "privateKey": "a40ffd19150b4f3cbb1ca779862fc63b15d432c0be9bba81c56856d00e370b91",
      "publicKey": "04483333bf900b59a412c26a8cf287e122be5d2882d66263ce330a2c84e426fcf48dca4e189dbef15dc3511b049b7708c1e3a49e4904a6286ffcc6019bb27a4ca9"
    },
    {
      "address": "io19sypnkmj6agqqgusht07m35lvlhz4ruehetagk",
      "privateKey": "fd49783f8687379e3eb6e5778977044cc7e464dd16df8444b8643d3d636f7ebc",
      "publicKey": "04bcae59b817ec2924adef52088e9295bb040d1a34fe49e64b41ca56e2cbb3be115256975d2c1472b0a3b47bea720810de092ef4d209924ce09fa896b29588a90d"
    },
    {
      "address": "io1ehlhw6kedp5x8y04ddr7fl0cs68ns32hdxuvdl",
      "privateKey": "2c1bdc74c7ff03f08f2e2d3b65af9a54dc5addc42613670bd4bb1f0440cd9468",
      "publicKey": "04cd1ff13e20cbe83bc8759ce21404edc2a9b78c57f8d2ffc648f2213dfee98b61d9ebaffe03f32e7a13fbe319b1958c99ed701c3fa1046790f6af12f32262309b"
    }
  ]
}
```

### Create and store

`Usage: ioctl account createadd ALIAS`

```bash
➜  ioctl account createadd IOsenser
#IOsenser: Set password
#IOsenser: Enter password again
New account "IOsenser" is created.
Please Keep your password, or you will lose your private key.
```

### Update the Password

`Usage: ioctl account update (ALIAS|ADDRESS)`

```bash
➜  ioctl account update IOsenser
#IOsenser: Enter current password
#IOsenser: Enter new password
#IOsenser: Enter new password again
Account #IOsenser has been updated.
```

### Import a Private Key

`Usage: ioctl account import [key|keystore] ALIAS` Two options are available. If you use `key`,

```bash
➜  ioctl account import key whale
#whale: Enter your private key, which will not be exposed on the screen.
#whale: Set password
#whale: Enter password again
New account #whale is created. Keep your password, or your will lose your private key.

```

If you use `keystore`,

```javascript
➜  ioctl account import keystore whale

```

### Export a Private Key

`Usage: ioctl account export (ALIAS|ADDRESS)`

```javascript
➜  ioctl account export whale
Enter password #whale:
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

### Export the Public Key

`Usage: ioctl account exportpublic (ALIAS|ADDRESS)`

```
➜  ioctl account exportpublic tmp2
Enter password #io120au9ra0nffdle04jx2g5gccn6gq8qd4fy03l4:
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

### Delete Accounts

`Usage: ioctl account delete (ALIAS|ADDRESS)`

```
➜  ioctl account delete whale
** This is an irreversible action!
Once an account is deleted, all the assets under this account may be lost!
Type 'YES' to continue, quit for anything else.
yes
Enter password #io1t54nfdnpldaxkpm35f2gzh3rx6cakypmp5xfz5:
Account #io1t54nfdnpldaxkpm35f2gzh3rx6cakypmp5xfz5 has been deleted.
```

### List Accounts

`Usage: ioctl account list`

```
➜  ioctl account list
io1r2r0um9dw35922tptkuphseq43hq2knk3fjrlt - IOsenser
io17laykjt9qgafuxj58fuspuxzlv6y4qgxf82vnm - frank
io1l3wc0smczyay8xq747e2hw63mzg3ctp6uf8wsg
io14gnqxf9dpkn05g337rl7eyt2nxasphf5m6n0rd - 007
```

### Sign a Message

`Usage: ioctl account sign MESSAGE [-s SIGNER]`

```
➜  ioctl account sign "abcd" -s tmp2
Enter password #io120au9ra0nffdle04jx2g5gccn6gq8qd4fy03l4:
ec280f9f95ed5774fb042e69d92bfb685443dc99350d5460ecf1067d1cb539150903ff0d18cdd5072ce72765996e80c96df7ed86c2b887ce4d41aa8cc2dd0b0001
```

### Account Balance

`Usage: ioctl account balance (ALIAS|ADDRESS)`

```
➜  ioctl account balance IOsenser
io1r2r0um9dw35922tptkuphseq43hq2knk3fjrlt: 0.721 IOTX

```

```
➜  ioctl account balance io1l3wc0smczyay8xq747e2hw63mzg3ctp6uf8wsg
io1l3wc0smczyay8xq747e2hw63mzg3ctp6uf8wsg: 4689 IOTX

```

### Account Nonce

`Usage: ioctl account nonce (ALIAS|ADDRESS)`

```
➜  ioctl account nonce IOsenser
io1r2r0um9dw35922tptkuphseq43hq2knk3fjrlt:
Nonce: 0, Pending Nonce: 1
```

### IoTeX↔Eth Address Conversion

`Usage: ioctl account ethaddr (ALIAS|IOTEX_ADDRESS|ETH_ADDRESS)`

```
➜  ioctl account ethaddr io14gnqxf9dpkn05g337rl7eyt2nxasphf5m6n0rd
io14gnqxf9dpkn05g337rl7eyt2nxasphf5m6n0rd - 0xAA260324ad0DA6FA2231f0FfEC916A99bb00dd34
```

```
➜  ioctl account ethaddr 0xAA260324ad0DA6FA2231f0FfEC916A99bb00dd34
io14gnqxf9dpkn05g337rl7eyt2nxasphf5m6n0rd - 0xAA260324ad0DA6FA2231f0FfEC916A99bb00dd34

```

```
➜  ioctl account ethaddr John
io14gnqxf9dpkn05g337rl7eyt2nxasphf5m6n0rd - 0xAA260324ad0DA6FA2231f0FfEC916A99bb00dd34
```

### Private Key to Public Key

`Usage: ioctl account verify`

```
➜  ioctl account verify
Enter private key:
Address:  io1gh439pm67d4cwxt882xpylj75klys6esepml60
Public Key: 04ac93d2fffdf488659c3f58890f6ddc55818d50f884e515aa90b2b1ca1e0fc223f85c5a0dc8b9a55b9a282a1ba8a269a3426f168591b60c921380f7d6d34c1f4f
```

### List Actions

Lists IOTX actions for an account. Outputs pages of 15 actions each, optionally skipping the first `SKIP` actions.&#x20;

{% hint style="warning" %}
This command is incomplete. It won't list less than 15 actions, and the**`SKIP`** argument must be set such that the output always contains at least 15 actions.
{% endhint %}

`usage: ioctl account actions (ALIAS|ADDRESS) [SKIP]`

```
➜ ioctl account actions devaccount
Total: 68
Hash                                                              Time                           Status                Sender                                     Type       To                                         Contract                                   Amount    
5f495b1641cec3648efb4d30d2b51e37952efd27d6592a5714b73a4b70b5c9d8  2021-05-19 10:41:05 +0000 UTC  Success               io1a8r9fvu6e3vthfaqvnxlhc6eavsm6t8a2cwtud  Transfer   io1kd7rq429sexntf323yjz4ft2ugmcj43hsw9tpf  io1enfa3p3aysdueq85vvprzzndjs4fp6z32hf7xs  10 IOTX   
1e4a97ce4fd70fbb6d339a739cc6c8d5b01f989f528f5abe0835824b87298290  2021-05-15 23:05:00 +0000 UTC  Success               io1a8r9fvu6e3vthfaqvnxlhc6eavsm6t8a2cwtud  Transfer   io1ysz9mccgz5emzj59n27js856gkmldxunxtgan7  io1enfa3p3aysdueq85vvprzzndjs4fp6z32hf7xs  1 IOTX    
aa4319ae73c08dedc9f950142025023986758f0ee5a874fbafd3fe6efb95c02f  2021-05-13 16:25:05 +0000 UTC  Success               io1a8r9fvu6e3vthfaqvnxlhc6eavsm6t8a2cwtud  Transfer   io1rl3j9gzuk5hjaykf28euphxg0yzjdk2gw27hel  io1enfa3p3aysdueq85vvprzzndjs4fp6z32hf7xs  5 IOTX    
9adbfa463b63eb027140a5f5e5884471d6b39721d09f8168446bfddba7c61224  2021-05-13 16:22:50 +0000 UTC  Success               io1a8r9fvu6e3vthfaqvnxlhc6eavsm6t8a2cwtud  Transfer   io1rl3j9gzuk5hjaykf28euphxg0yzjdk2gw27hel  io1enfa3p3aysdueq85vvprzzndjs4fp6z32hf7xs  5 IOTX    
cf3921a6a8bca11b89fa6ba9fea5ad9b84304b08844976216ed96ab985105f4a  2021-05-11 15:38:20 +0000 UTC  Success               io1a8r9fvu6e3vthfaqvnxlhc6eavsm6t8a2cwtud  Transfer   io1jzdxuv7etyfvs7th7jwyspswr6y660zjd7lykg  io1enfa3p3aysdueq85vvprzzndjs4fp6z32hf7xs  1 IOTX    
ad577bb9d165aee4dd16a6178fb14da06f132b963745d56779aef75833a7bb67  2021-05-03 17:02:25 +0000 UTC  Success               io1a8r9fvu6e3vthfaqvnxlhc6eavsm6t8a2cwtud  Transfer   io1ludk0lclyxx9yaaae09zap0x9p9zwjcy6z7juq  io1enfa3p3aysdueq85vvprzzndjs4fp6z32hf7xs  5 IOTX    
ca6c33a0fb9ce4677b58d8db9372142f3a4c03e2654792a9e8b2c42d9738ba6b  2021-04-26 13:21:45 +0000 UTC  Success               io1a8r9fvu6e3vthfaqvnxlhc6eavsm6t8a2cwtud  Transfer   io1jvlmwxhxupdxc34886hxr24daks0vmtwtl6szf  io1enfa3p3aysdueq85vvprzzndjs4fp6z32hf7xs  3 IOTX    
c5ca57620831fb0680d233405f2bdd37760356f4bdccaeee39e6bf997c0080bb  2021-04-25 22:36:40 +0000 UTC  Success               io1a8r9fvu6e3vthfaqvnxlhc6eavsm6t8a2cwtud  Execution  -                                          io1c7wdq5j5k6eaw924ug8md38uvj2jfq4753s6nz  0 IOTX    
5b449a7b3238dfa3acc6e08c056bc5d04c1ff62846e5101a20cddd4d0892b1bb  2021-04-14 18:03:00 +0000 UTC  Success               io1u8y0z2gnctvhzm0qhm7uwey8j2k9lgyprr0ydl  Transfer   io1a8r9fvu6e3vthfaqvnxlhc6eavsm6t8a2cwtud  io1enfa3p3aysdueq85vvprzzndjs4fp6z32hf7xs  100 IOTX  
0a2a4399e39507265e6dc8fedc4dba47a8d3bac921e7b7e71b9676613a12a2fc  2021-04-14 17:58:50 +0000 UTC  Success               io1a8r9fvu6e3vthfaqvnxlhc6eavsm6t8a2cwtud  Transfer   io1u8y0z2gnctvhzm0qhm7uwey8j2k9lgyprr0ydl  io1enfa3p3aysdueq85vvprzzndjs4fp6z32hf7xs  2 IOTX    
29d35f02cc21631655a4004cfa5b1b184a7d0d0cc9f5b37d0a546bd956c4ef83  2021-03-26 16:15:20 +0000 UTC  ErrExecutionReverted  io1a8r9fvu6e3vthfaqvnxlhc6eavsm6t8a2cwtud  Execution  io1jq982lhl4z3wq4gqz7d9hk2tz8hpmptwejwjg7  -                                          0 IOTX    
63e2a1a5bfa13ac0d826d9e59cea77ced76d56373f4a931146f24cc2da0172ac  2021-03-26 16:14:55 +0000 UTC  Success               io1a8r9fvu6e3vthfaqvnxlhc6eavsm6t8a2cwtud  Execution  io1jq982lhl4z3wq4gqz7d9hk2tz8hpmptwejwjg7  -                                          0 IOTX    
63546afc4286eed15b78495af3de8b376d60776d374f7a1be64746437dee028e  2021-03-26 16:13:40 +0000 UTC  Success               io1a8r9fvu6e3vthfaqvnxlhc6eavsm6t8a2cwtud  Execution  -                                          io1jq982lhl4z3wq4gqz7d9hk2tz8hpmptwejwjg7  0 IOTX    
5c64668a0c16e7e1fc19f278668a8f9111a44c663b4d1bd18b13e3128345e1bb  2021-03-26 16:12:15 +0000 UTC  ErrExecutionReverted  io1a8r9fvu6e3vthfaqvnxlhc6eavsm6t8a2cwtud  Execution  io1m5900gwt99ca0r7n98txaw67apg5ssf2hehwj4  -                                          0 IOTX    
34ea3964df5d7b3ca918953e3213b3b185c69b27065ec1107b094e05845fd7ba  2021-03-26 16:11:45 +0000 UTC  Success               io1a8r9fvu6e3vthfaqvnxlhc6eavsm6t8a2cwtud  Execution  io1m5900gwt99ca0r7n98txaw67apg5ssf2hehwj4  -                                          0 IOTX    
```

```
➜ ioctl account actions devaccount 53
Total: 68
Hash                                                              Time                           Status                Sender                                     Type       To                                         Contract                                   Amount    
40eb9ed83f3e7f9d3597fc9c332e42a929550046236c3090273df85d019b4403  2020-12-07 19:06:25 +0000 UTC  Success               io1dvfjg5xxnzpydnmq2q0n0n0ham2arytkkvrr2h  Transfer   io1a8r9fvu6e3vthfaqvnxlhc6eavsm6t8a2cwtud  io1enfa3p3aysdueq85vvprzzndjs4fp6z32hf7xs  0.1 IOTX  
fe5a745f34fcf396a8ead53e0826b51198130204d0617a3642e04a876f7b4aba  2020-12-07 19:06:10 +0000 UTC  Success               io1a8r9fvu6e3vthfaqvnxlhc6eavsm6t8a2cwtud  Transfer   io1a8r9fvu6e3vthfaqvnxlhc6eavsm6t8a2cwtud  io1enfa3p3aysdueq85vvprzzndjs4fp6z32hf7xs  0.1 IOTX  
fa5dd1088a62201d9bc023d83d45d2f6cdac7dfff137c722a44f474f80a55297  2020-12-07 16:04:15 +0000 UTC  Success               io1a8r9fvu6e3vthfaqvnxlhc6eavsm6t8a2cwtud  Execution  io1qvvzehk42l0g86xwnrszjhna53urpa7zwex80t  -                                          0 IOTX    
2f7d0bcb7e7a92742efd5b63bd0b396f884bc296a14f29bb675a0ae3afb71498  2020-12-07 15:51:55 +0000 UTC  ErrExecutionReverted  io1a8r9fvu6e3vthfaqvnxlhc6eavsm6t8a2cwtud  Execution  io1qvvzehk42l0g86xwnrszjhna53urpa7zwex80t  -                                          0 IOTX    
4b614079303bf6f06195127f10967cd24174b726277f62f80a099f9027914731  2020-12-07 15:46:45 +0000 UTC  ErrExecutionReverted  io1a8r9fvu6e3vthfaqvnxlhc6eavsm6t8a2cwtud  Execution  io1qvvzehk42l0g86xwnrszjhna53urpa7zwex80t  -                                          0 IOTX    
ef3c3d7b394f7bde21a9118d24ced01195b2b19ddc28c639897b4ebce8569cbd  2020-12-04 23:41:20 +0000 UTC  ErrExecutionReverted  io1a8r9fvu6e3vthfaqvnxlhc6eavsm6t8a2cwtud  Execution  io1rvjnvt6pzvtlsf08cnfn95kxdmhc2vvvewjf7e  -                                          0 IOTX    
062eee49c27565e340c216b16ec31fcef0dc11220b961a005534331c1d3470af  2020-12-04 23:40:45 +0000 UTC  Success               io1a8r9fvu6e3vthfaqvnxlhc6eavsm6t8a2cwtud  Execution  io1rvjnvt6pzvtlsf08cnfn95kxdmhc2vvvewjf7e  -                                          0 IOTX    
4ac34b49a62fce82f0a81053cac070ddc3ebcb63713c5fb440b88b924b69f95a  2020-12-04 22:45:50 +0000 UTC  Success               io1a8r9fvu6e3vthfaqvnxlhc6eavsm6t8a2cwtud  Execution  io1rvjnvt6pzvtlsf08cnfn95kxdmhc2vvvewjf7e  -                                          0 IOTX    
0593eea7e354ce1240d77eb1f72222288787585c153d87a9280b37c9e60188d6  2020-12-04 22:32:10 +0000 UTC  Success               io1a8r9fvu6e3vthfaqvnxlhc6eavsm6t8a2cwtud  Execution  -                                          io1rvjnvt6pzvtlsf08cnfn95kxdmhc2vvvewjf7e  0 IOTX    
5ff55671173b11430593a9e12a0068ef14f64ead01cb40f0e755a4776924507f  2020-12-04 17:19:25 +0000 UTC  Success               io1a8r9fvu6e3vthfaqvnxlhc6eavsm6t8a2cwtud  Execution  io12rcmdvmd5htqces0p9jxr5d99gvzplty2dvc7a  -                                          0 IOTX    
7023c27b0e31f2391486fa9eadc83bb66902edb0c94460947c8ca37e864c3fc4  2020-12-04 17:18:55 +0000 UTC  Success               io1dvfjg5xxnzpydnmq2q0n0n0ham2arytkkvrr2h  Transfer   io1a8r9fvu6e3vthfaqvnxlhc6eavsm6t8a2cwtud  io1enfa3p3aysdueq85vvprzzndjs4fp6z32hf7xs  50 IOTX   
aff549058c77b50c2663c449e4e83473395c23189a6e8b627f219bd8f4506fc0  2020-12-04 16:48:20 +0000 UTC  Success               io1a8r9fvu6e3vthfaqvnxlhc6eavsm6t8a2cwtud  Execution  io12wm2lz8z3jac2ey9fa6eemmejm24qsghugnmfr  -                                          0 IOTX    
9869c9215e9faa857d7b953a30ff99bbf14cb76f1fce99f828b3ea7bad7aa980  2020-12-04 16:31:20 +0000 UTC  Success               io1a8r9fvu6e3vthfaqvnxlhc6eavsm6t8a2cwtud  Execution  -                                          io12rcmdvmd5htqces0p9jxr5d99gvzplty2dvc7a  0 IOTX    
a4ce0a15665399296dbfbb4ce7aeae32a24eb1e12bbd4cba67d22a1bd800afcd  2020-12-04 16:30:35 +0000 UTC  Success               io1dvfjg5xxnzpydnmq2q0n0n0ham2arytkkvrr2h  Transfer   io1a8r9fvu6e3vthfaqvnxlhc6eavsm6t8a2cwtud  io1enfa3p3aysdueq85vvprzzndjs4fp6z32hf7xs  15 IOTX   
4c734ccac1fa25f627c2e7cc5818b0354ae37b751cc90001c29f47ff00d6cf11  2020-08-17 11:45:25 +0000 UTC  Success               io1dvfjg5xxnzpydnmq2q0n0n0ham2arytkkvrr2h  Transfer   io1a8r9fvu6e3vthfaqvnxlhc6eavsm6t8a2cwtud  io1enfa3p3aysdueq85vvprzzndjs4fp6z32hf7xs  5 IOTX   
```
