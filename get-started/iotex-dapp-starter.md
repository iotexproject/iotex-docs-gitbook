# IoTeX dApp Sample

## Introduction 

The **IoTeX dApp Sample** is a comfortable environment for **learning IoTeX **development and is the best way to build **a new dApp**.

It sets up a basic working example that is cross-blockchain, multi-asset and supports the most popular wallet apps  (including [Metamask](https://metamask.io)) out of the box. The example utilizes the latest JavaScript features, provides a nice developer experience and optimizes your app for production. You’ll need to have [Node>=10.17.0](https://nodejs.org/en/). 

![IoTeX dApp Starter](<../.gitbook/assets/image (55).png>)

This sample dApp supports Typescript as includes [Vite](https://vitejs.dev/guide/why.html) as a fast build server, [React](https://reactjs.org) as the frontend framework, [Chakra](https://chakra-ui.com) as a components library, and [Cypress](https://www.cypress.io) as a testing suite.

## Get Started

To start your **IoTeX dApp,** you can fork the dApp Sample repository: 

1. **Open the repository on GitHub:** [https://github.com/iotexproject/iotex-dapp-sample-v2](https://github.com/iotexproject/iotex-dapp-sample-v2).
2. Click the "**Use this template**" button:

![](<../.gitbook/assets/image (56).png>)

   3\. Clone your new repository: 

```
git clone https://github.com/<your-github-username>/iotex-dapp-sample-v2.git
```

Once the repository is cloned, you can start the demo app with:

```bash
cd iotex-dapp-sample-v2
yarn install
yarn start
```

See the demo app running on your local machine at [localhost:3000, ](http://localhost:3000)and start building your great new idea!

## Cheatsheet

Here's a cheat sheet as a reference:

```typescript
import { rootStore, useStore } from '@/store/index';

const { god } = useStore()
// or const god = rootStore.god

god.isConnect   

god.currentChain 
god.currentChain.chainId  // for current connected chain id 
god.currentChain.Coin  // eth/bnb/iotx
god.currentChain.Coin.balance  // current balance
// ... see ChainState

god.currentNetwork     
god.currentNetwork.account   // for current connected account address
// ... see NetworkState
 

god.setShowConnecter()  // to show/close the Wallet Selector

god.currentNetwork.loadBalance() // to load chain coin balance
god.currentNetwork.multicall()  // main function to batch read state from contract
god.currentNetwork.execContract() // main function to execute contract 


// multicall/execContract example
import ERC20ABI from "..."

const newToken = {
    address: "0x810ee35443639348adbbc467b33310d2ab43c168",
    abi: ERC20ABI, 
    symbol: "",
    name: "",
    decimals: "",
    balance: new BignumberState({}),
}

const {address, abi} = newToken

await god.currentNetwork.multicall([
    { address, abi, method: 'symbol', handler: (v: any) => (newToken.symbol = v.toString()) },
    { address, abi, method: 'name', handler: (v: any) => (newToken.name = v.toString()) },
    { address, abi, method: 'decimals', handler: (v: any) => (newToken.decimals = Number(v.toString())) },
    { address, abi, method: 'balanceOf', params:[god.currentNetwork.account]  handler: newToken.balance},
);

await god.currenNetwork.execContract({adderss,abi,method:"transfer", params:["0x", "100000000000000000"]})
await god.currenNetwork.execContract({adderss,abi,method:"approve", params:["0x", "100000000000000000"]})



// to help share the bignumber between on function and UI
import BN from 'bignumber.js';
import { BigNumberState } from '@/store/standard/BigNumberState';

const tokenAmount = new BigNumberState({value: new BN(1000000000000000000), decimals: 18 })
console.log(tokenAmount.value.toFixed(0), tokenAmount.format)
// 1000000000000000000, 1
tokenAmount.setValue(new BN(2000000000000000000))
// 2000000000000000000, 2

```
