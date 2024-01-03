# Command line client

## Overview

**ioctl** is the IoTeX official command line client, and it's the Swiss Army knife for any IoTeX developer.&#x20;

In addition to being a multi-account wallet also supporting staking, ioctl provides a wide variety of advanced functions to interact with the IoTeX blockchain.&#x20;

ioctl can be used within Bash scripts to send actions and make requests to the blockchain, interact with smart contracts and more.

Check out this introductory video about using **ioctl** as a command line IoTeX wallet:&#x20;

{% embed url="https://www.youtube.com/watch?v=Q-je019KGUA" %}

This section will go through some of the basic commands you need to get started with **ioctl** and the IoTeX Blockchain!&#x20;

{% hint style="success" %}
For the full ioctl commands reference, check out the dedicated page:
{% endhint %}

{% content-ref url="../../../../backlog/reference/ioctl-cli-reference/" %}
[ioctl-cli-reference](../../../../backlog/reference/ioctl-cli-reference/)
{% endcontent-ref %}

## Install ioctl

You can easily download and install the latest releases of **ioctl** by typing the following command in a terminal window:

{% tabs %}
{% tab title="Linux" %}
Using `curl`:

```bash
# install ioctl latest stable
curl https://raw.githubusercontent.com/iotexproject/iotex-core/master/install-cli.sh | sh

# install ioctl latest unstable build
curl https://raw.githubusercontent.com/iotexproject/iotex-core/master/install-cli.sh | sh -s "unstable"
```
{% endtab %}

{% tab title="macOS" %}
Using `brew`:

```bash
# install ioctl latest stable
brew install ioctl

# install ioctl latest unstable build
brew install ioctl-unstable
```

Using `curl`:

```bash
# install ioctl latest stable
curl https://raw.githubusercontent.com/iotexproject/iotex-core/master/install-cli.sh | sh

# install ioctl latest unstable build
curl https://raw.githubusercontent.com/iotexproject/iotex-core/master/install-cli.sh | sh -s "unstable"
```
{% endtab %}

{% tab title="Windows" %}
{% hint style="danger" %}
Currently, **ioctl** is not supported on Windows systems.
{% endhint %}
{% endtab %}
{% endtabs %}

Once ioctl is installed in your system, you must configure the endpoint of an IoTeX full node that acts as a Gateway to the network. Anyone can install an IoTeX full node and configure it as a gateway. Here we will use the public endpoints provided by the IoTex team for the mainnet and testnet networks:

```bash
# Point ioctl to the IoTeX Mainnet
ioctl config set endpoint api.mainnet.iotex.one:443

# Point ioctl to the IoTeX Testnet
ioctl config set endpoint api.testnet.iotex.one:443
```

## Create a new account

Let's begin with creating a new IoTeX wallet [account](../../../../backlog/basic-concepts/accounts.md): similarly to any blockchain wallet app where you can "_create a new wallet"_, this operation consists of [generating a random private key](../../../../backlog/basic-concepts/accounts-cryptography.md) and storing it in an encrypted file, protected by a password of your choice. It also allows you to set an _alias_ for the newly created account (we will use the alias "_dev-acc_" alias in the following sections). Once the alias is set, it can be used instead of the account address in any **ioctl** command:

Create and store an IoTeX account and assign the "dev-acc" alias to it with command below:

```
ioctl account createadd dev-acc
```

**ioctl** will ask you to provide a password that will be used to encrypt your newly created account. From now on when using **ioctl** commands you can refer to this account by using the alias **dev-acc** and the password of your choice.

{% hint style="danger" %}
It's highly recommended that you get used to immediately backup your account passwords in a safe place when you create a new account. Losing your password means losing access to the private key: when you interact with the IoTeX mainnet, **losing access to your private key means you will lose all the funds that you have sent to that account. Forever!**
{% endhint %}

{% hint style="info" %}
### Where does ioctl store accounts data?

All accounts created in **ioctl**, as well as all the aliases, and other settings are stored locally on your computer, in the following path:

`~/.config/ioctl`

You can make a copy of this folder to port your **ioctl** settings and accounts to multiple computers.
{% endhint %}

## Interact with the Blockchain

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

Send **10 IOTX** from your _dev-acc_ account to the recipient address **io1mflp9m6hcgm2qcghchsdqj3z3eccrnekx9p0ms with the command** `ioctl account transfer:`

```
ioctl action transfer io1mflp9m6hcgm2qcghchsdqj3z3eccrnekx9p0ms 10 -s dev-acc
```

**ioctl** will then ask for the password of your _dev-acc_ account, then it will broadcast the action to the blockchain by sending it to the gateway node, and finally provide the hash of the action for you to check the status.

Finally, check the status of a transaction by its hash with the command `ioctl action hash`:

```
ioctl action hash bc84a8e6531b7ccacb317cbf9f53a59ee9b0e14db44f6ca940546a4ab5dfd1e6
```
