# Interact with the blockchain

Now that you have ioctl pointing to an IoTeX gateway and a wallet account configured in your system, let's try some basic interactions with the Blockchain:

Check the blockchain current epoch, height, and other network-related meta-information with the command `ioctl bc info`:

```
$ ioctl bc info

Blockchain Node: localhost:14014
{
  "height": 126,
  "numActions": 126,
  "tps": 1,
  "tpsFloat": 0.0021198923
}

```

Verify the balance of your account with the command `ioctl account balance`:

```
$ ioctl account balance dev-acc

io1a8r9fvu6e3vthfaqvnxlhc6eavsm6t8a2cwtud: 100000000000000000000000000000000000 IOTX
```

Send **10 IOTX** from your _dev-acc_ account to the recipient address **io1mflp9m6hcgm2qcghchsdqj3z3eccrnekx9p0ms with the command **`ioctl account transfer:`

```
ioctl action transfer io1mflp9m6hcgm2qcghchsdqj3z3eccrnekx9p0ms 10 -s dev-acc
```

**ioctl** will then ask for the password of your _dev-acc_ account, then it will broadcast the action to the blockchain by sending it to the gateway node, and finally provide the hash of the action for you to check the status.

Finally, check the status of a transaction by its hash with the command `ioctl action hash`:

```
ioctl action hash bc84a8e6531b7ccacb317cbf9f53a59ee9b0e14db44f6ca940546a4ab5dfd1e6
```
