# Deploy Using Remix

The easiest way to deploy an XRC20 token on IoTeX is using the Remix IDE in conjunction with Metamask.

## 1. Configure Metamask

Make sure you configured Metamask for use with the IoTeX Blockchain and that the IoTeX network, whether its mainnet or testnet, is actually selected in Metamask:

{% page-ref page="../../get-started/iotex-wallets/metamask.md" %}

## 2. Open Remix IDE and paste the code

Open the [Remix IDE](https://remix.ethereum.org/) and create a new file under the `Contracts` folder: call it `Simpletoken.sol` and paste the [source code](./#the-source-code) of the token, then save the file:

![](../../.gitbook/assets/image%20%2860%29.png)

## 3. Compile the contract

Move to the "_Solidity Compiler"_ tab in the left navigator, select the correct compiler version for the contract, and compile the contract:

![](../../.gitbook/assets/image%20%2861%29.png)

## Deploy the contract

Switch the the "_Deploy & Run Transactions_" tab, select "_Injected Web3_" as the environment to make Remi use your Metamask account to run transactions, then click the "_Deploy_" button and finally confirm the deployment transaction in Metamask \(make sure [you have some IOTX](../../get-started/iotx-faucets.md) to pay for gas in your Metamask wallet! 

![](../../.gitbook/assets/image%20%2857%29.png)

## Interact with the Contract

Once the contract is deployed, you can easily interact with it directly in the Remix UI. For example, you can query the balance of the contract creator address, which should have received the entire total supply of the token upon deployment.

Look for the "_SimpleToken_" deployed contract in the left panel and expand it. Input the address you used to deploy the contract in the arguments field of the "`balanceOf`" function, click the "`balanceOf`" button to actually execute the contract call, and you should see the balance of SIM for your account right below the button:

![](../../.gitbook/assets/image%20%2858%29.png)

