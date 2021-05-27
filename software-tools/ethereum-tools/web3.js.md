# Web3.js

[web3.js](https://web3js.readthedocs.io/en/v1.2.11/) is a collection of libraries that allow you to interact with a local or remote ethereum node using HTTP, IPC or WebSocket. This guide describes how to configure Web3.js when you want to develop DApps using Web3 with the IoTeX Network.

### Connect to the IoTeX network <a id="connect-to-bsc-network"></a>

```javascript
// mainnet 
const web3 = new Web3('https://babel-api.mainnet.iotex.io');
// testnet
const web3 = new Web3('https://babel-api.testnet.iotex.io');
```

### Create an account <a id="set-up-account"></a>

If the installation and instantiation of web3 was successful, the following should successfully return a random account:

```javascript
const account = web3.eth.accounts.create();
```

### Import a private key <a id="recover-account"></a>

If you have backup the private key of your account, you can use it to restore your account.

```javascript
const account = web3.eth.accounts.privateKeyToAccount(privateKey)
```

### Full Example <a id="full-example"></a>

Initialize a new nodejs app:

```bash
mkdir Web3Test
cd Web3Test
npm init -y
npm install web3 big.js -s
```

then edit index.js as below:

```javascript
// index.js

const Web3 = require('web3');
const Big = require('big.js');

// Initialize web3.js using the IoTeX Babel endpoint
const web3 = new Web3(new Web3.providers.HttpProvider("https://babel-api.testnet.iotex.io"));

// Create a brand new account
const account = web3.eth.accounts.create();
console.log("Account created: %s", account.address);

// Query the balance of the IoTeX address io1qz02qneamgdseprun3eswcudg2runs4kwpv842
// You can use "ioctl account ethaddr <address>" to convert to Eth address format:
let address = "0x009EA04f3dda1b0C847c9C7307638d4287c9C2B6"
web3.eth.getBalance(address).then(
    function (balance) {
        let iotxBalance = Big(balance).div(10**18);
        console.log("Balance of %s is %s IOTX",address,iotxBalance.toFixed(18))
    });  
```

Run the example:

```javascript
node index.js
```

