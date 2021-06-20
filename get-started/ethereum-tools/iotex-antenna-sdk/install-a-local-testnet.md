# Configure a local IoTeX Testnet

### Build the node server <a id="build-the-node-server"></a>

Before you start your journey as an IoTeX developer, you need an IoTeX [Gateway node](https://docs.iotex.io/introduction/node-concept) to serve as an **endpoint**, that you can use to interact with the blockchain. While IoTeX provides official gateway nodes both to interact with Mainnet and Testnet, in this guide we will configure our own local Testnet, which will also include pre-generated accounts with some balance to start with.

To configure an IoTeX blockchain node locally on your computer, you will need git and Golang installed: you can get [more instructions on GitHub](https://github.com/iotexproject/iotex-core#iotex-core).

Clone and build the IoTeX Full-Node code \(iotex-core\)

```text
git clone https://github.com/iotexproject/iotex-core.git
cd iotex-core
make
```

### Add a test account with an initial balance <a id="add-a-test-account-with-initial-balance"></a>

Now that the node executable is built in the .bin/ directory, the last step is to add an initial test account preloaded with IOTX tokens. We will use our [dev-acc](https://docs.iotex.io/ioctl-create-account) account:

```text
$ ioctl account list

io1a8r9fvu6e3vthfaqvnxlhc6eavsm6t8a2cwtud - dev-acc
```

edit the genesis file `./config/standalone-genesis.yaml` and add this account to the `initBalances` section:

```text
account:
  initBalances:
    # overwrite with your test address
    io1a8r9fvu6e3vthfaqvnxlhc6eavsm6t8a2cwtud: "100000000000000000000000000000000000"
```

we can now start our Testnet using the **STANDALONE** mode to simulate a full blockchain in a single node:

```text
make run
```

