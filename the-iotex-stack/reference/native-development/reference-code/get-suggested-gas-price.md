# Get Suggested Gas Price

Before sending a transaction to the blockchain, it's good practice to estimate a gas price that ensures the transaction is mined within a reasonable timeframe, particularly during periods of network congestion. The IoTeX API's `suggestGasPrice` call provides a basic estimation of this cost. Below is an example of how to use this function:

```javascript
const Antenna = require("iotex-antenna").default;

// Create an async main function to utilize 'await'
async function main() {
    // Initialize a new Antenna instance
    const antenna = new Antenna("https://api.mainnet.iotex.one");
    // Call suggestGasPrice to get the gas estimation
    const gasPrice = await antenna.iotx.suggestGasPrice();
    console.log(gasPrice);
}

main();


```
