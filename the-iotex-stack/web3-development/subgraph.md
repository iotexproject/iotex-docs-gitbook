# Subgraph

## Introduction

[The Graph](https://thegraph.com/docs/en/about/) is a decentralized protocol for indexing and querying data from blockchains, making it possible to query data that is difficult to query directly. In the Graph architecture, Indexers are the primary service provider for data queries: they store and index data, and provide the indexed data as a P2P pay-per-call API service.

To learn more about how The Graph works, we refer yo to the official documentation website:

{% embed url="https://thegraph.com/docs/en/" %}

## Run an IoTeX Indexer Node

If you want to use **The Graph** to query the blockchain data needed for your IoTeX dApp, you can run your Graph Indexer Node by simply editing the `graph-node/docker/docker-compose.yml` configuration file such that it points to the a Babel service, the Ethereum-Compatible API Gateway for IoTeX:

```yaml
services:
  graph-node:
    environment:
      ethereum: 'mainnet:https://babel-api.mainnet.iotex.io'
```

You can set `ethereum: testnet:https://babel-api.testnet.iotex.io` if you want to work with the IoTeX testnet instead.

For more information about how to run a Graph Indexer node, please refer to the official documentation at:

{% embed url="https://thegraph.com/docs/en/network/indexing/" %}

## Deploy a Subgraph

Once you have your Indexer Node running, you can define and locally deploy your Subgraphs as usual. Please refer to the official Subgraph quick start guide at:

{% embed url="https://thegraph.com/docs/en/quick-start/" %}

## Official hosted service

### Common Subgraph

* Blocks [https://graph.mainnet.iotex.io/subgraphs/name/common/blocks/graphql](https://graph.mainnet.iotex.io/subgraphs/name/common/blocks/graphql)

### Deploy

```
graph create common/blocks --node https://rpc.graph.mainnet.iotex.io/
graph deploy --debug --ipfs https://ipfs.mainnet.iotex.io --node  https://rpc.graph.mainnet.iotex.io/ common/blocks subgraphs/blocks.yaml
```
