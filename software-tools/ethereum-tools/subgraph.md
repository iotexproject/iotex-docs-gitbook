# Subgraph

This guide describes how to configure [Subgraph](https://thegraph.com/docs/introduction) so that you can deploy dApps on the IoTeX Network. Since Subgraph works in conjunction with Truffle, you should correctly [configure Truffle to work with the IoTeX Network first](truffle.md). Assuming that Truffle is correctly configured, and that the [Babel](../../reference/babel-web3-api.md) endpoint is set to [https://babel-api.mainnet.iotex.io:8545](https://babel-api.mainnet.iotex.io:8545/), you simply need to edit the `graph-node/docker/docker-compose.yml` configuration file as below:

```text
services:
  graph-node:
    environment:
      ethereum: 'mainnet:https://babel-api.mainnet.iotex.io'
```

