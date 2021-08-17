# Action Injector

Action injector is a simulation tool to simulate action traffic by injecting random actions to the gateway node.

## Get the source code

You find the source code in the iotex-core GitHub repository, under the "tools" directory:

{% embed url="https://github.com/iotexproject/iotex-core/tree/812b27f3b960074ecb49750b3be0850f641119e8/tools/actioninjector.v2" %}

## Build the injector

Clone the iotex-core repository and build the tool like below:

```bash
git clone https://github.com/iotexproject/iotex-core.git
cd iotex-core
cd tools
cd actioninjector.v2
./build_injector.sh 
```

After the tool is built, the executable can be found in the `release/forlder`. Type the following to get the allowed options:

{% tabs %}
{% tab title="MacOS" %}
`release/injector-darwin-amd64 inject --help`
{% endtab %}

{% tab title="Linux" %}
`release/injector-linux-amd64 inject --help`
{% endtab %}
{% endtabs %}

Output:

```bash
inject actions [options : -m] (default:random).

Usage:
  injector inject [flags]

Flags:
      --action-type string            action type to inject (default "transfer")
      --addr string                   target ip:port for grpc connection (default "127.0.0.1:14014")
      --aps int                       actions to be injected per second (default 30)
      --check-recipt                  check recept
      --contract string               smart contract address (default "io1pmjhyksxmz2xpxn2qmz4gx9qq2kn2gdr8un4xq")
      --duration duration             duration when the injection will run (default 60h0m0s)
      --execution-amount int          execution amount
      --execution-gas-limit uint      execution gas limit (default 100000)
      --execution-gas-price int       execution gas price
  -h, --help                          help for inject
      --injector-config-path string   path of config file of genesis transfer addresses (default "./tools/actioninjector.v2/gentsfaddrs.yaml")
      --insecure                      insecure network
      --load-token-amount int         init load how much token to inject accounts
      --rand-accounts int             number of accounst to use (default 3000)
      --reset-interval duration       time interval to reset nonce counter (default 10s)
      --retry-interval duration       sleep interval between two consecutive rpc retries (default 1s)
      --retry-num uint                maximum number of rpc retries (default 5)
      --transfer-amount int           execution amount
      --transfer-gas-limit uint       transfer gas limit (default 20000)
      --transfer-gas-price int        transfer gas price
      --workers uint                  number of workers (default 10)
```

The file `gentsfaddrs.yaml` includes the list of accounts used by the tool

**Note:** in case during the execution you come ove error messages such as "_action is not found_", check the following:

1. Incorrect nonce \(too small or too large\)
2. Too low gas price
3. Too small gas limit
4. Account balance not enough \(amount + gas price \* gas limit\)

