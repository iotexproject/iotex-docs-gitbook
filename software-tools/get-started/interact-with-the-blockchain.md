# Interact with the blockchain

Now that you have a local IoTeX gateway node running in your terminal window \(and simulating an entire Testnet in itself!\), let's start interacting with it using the **ioctl** command-line client.

Point **ioctl** to your local gateway node:

```text
ioctl config set endpoint localhost:14014 --insecure
```

Check the blockchain current epoch, height, and other meta information:

```text
$ ioctl bc info

Blockchain Node: localhost:14014
{
  "height": 126,
  "numActions": 126,
  "tps": 1,
  "tpsFloat": 0.0021198923
}

```

Verify the balance of your account:

```text
$ ioctl account balance dev-acc

io1a8r9fvu6e3vthfaqvnxlhc6eavsm6t8a2cwtud: 100000000000000000000000000000000000 IOTX
```

