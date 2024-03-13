# Contract Verification

## Introduction

Smart contracts aim to be trustless, requiring users to trust the contract execution without depending on third parties. This is ensured through source code verification, allowing users to confirm that some source code matches the code executed on the IoTeX blockchain.&#x20;

Source code verification differs from formal verification, which checks if the contract behaves as intended. Typically, "contract verification" refers to the former, focusing on the match between high-level source code and the blockchain's bytecode.

{% hint style="success" %}
In this tutorial, we will guide you through the entire process of verifying a smart contract using [IoTeXscan](https://iotexscan.io/verify-contract). Starting with contract creation, we'll then deploy it to the IoTeX testnet, and conclude by verifying the contract through [Hardhat](https://hardhat.org/hardhat-runner/docs/guides/verifying).
{% endhint %}

## Setting Up a Hardhat Project

1. **Install NodeJS:** Ensure NodeJS is installed on your system.
2.  **Install Hardhat:** Execute the following command to install Hardhat:

    ```css
    npm install --save-dev hardhat
    ```
3.  **Initialize a Hardhat Project:** To start a new Hardhat project, run:

    <pre class="language-csharp"><code class="lang-csharp"><strong>npx hardhat init
    </strong></code></pre>

    For further details on creating smart contracts with Hardhat, refer to the official tutorial.

## Coding the Contract

1.  **Create the Contract File:** Inside your Hardhat project directory, navigate to the `contracts` subfolder and create a file named `greeter.sol`. Insert the following code:

    ```solidity
    // SPDX-License-Identifier: UNLICENSED pragma solidity ^0.8.0; 
    import "@openzeppelin/contracts/token/ERC1155/ERC1155.sol"; 

    contract NFT is ERC1155 { 
      constructor() ERC1155("URL") { 
        _mint(msg.sender, 0, 1, ""); 
      } 
    }
    ```
2.  **Install OpenZeppelin Contracts:** Run the following command to include the OpenZeppelin contracts package:

    ```bash
    npm install @openzeppelin/contracts
    ```
3.  **Compile Your Contract:** Compile the smart contract with:

    ```python
    npx hardhat compile
    ```

## Preparing for Deployment

1. **Setup IoTeX Testnet Account:** Ensure you have a developer account on the IoTeX testnet with a balance of test IOTX tokens. Visit the IoTeX documentation for instructions on account creation and funding.
2.  **Configure Hardhat:** Modify `hardhat.config.js` to add the IoTeX network configurations, including your IoTeX Developer account private key:

    ```javascript
    ...
    networks: {
        hardhat: {
        },
        mainnet: {
          url: 'https://babel-api.mainnet.IoTeX.io',
          accounts: [ PRIVATE_KEY ],
          chainId: 4689,
          gas: 8500000,
          gasPrice: 1000000000000
        },
        testnet: {
          url: 'https://babel-api.testnet.IoTeX.io',
          accounts: [ PRIVATE_KEY ],
          chainId: 4690,
          gas: 8500000,
          gasPrice: 1000000000000
        }
      },
      ...
    ```
3.  **Deploy Script:** Edit `scripts/deploy.js` with the following code to deploy your contract:

    ```javascript
    const hre = require("hardhat");

    async function main() {
      const NFT = await hre.ethers.deployContract("NFT");
      await NFT.waitForDeployment();
      console.log("NFT deployed to:", NFT.target);
    }

    main().catch((error) => {
      console.error(error);
      process.exitCode = 1;
    });
    ```
4.  **Deploy the Contract:** Deploy your contract to the IoTeX testnet by running:

    ```sh
    npx hardhat run scripts/deploy.js --network testnet
    ```

    Note the contract address provided in the deployment log.

## Verifying the Contract

1.  **Install hardhat-verify Plugin:** To enable contract verification, install the hardhat-verify plugin:

    ```css
    npm install --save-dev @nomicfoundation/hardhat-verify
    ```
2.  **Update Hardhat Configuration:** Edit `hardhat.config.js` by adding the configuration for contract verification, make sure you use your API key:

    ```javascript
    etherscan: {
        apiKey: "YOUR_ETHER",
        customChains: [
          {
            network: "mainnet",
            chainId: 4689,
            urls: {
              apiURL: "https://IoTeXscout.io/api",
              browserURL: "https://IoTeXscan.io"
            }
          },
          {
            network: "testnet",
            chainId: 4690,
            urls: {
              apiURL: "https://testnet.IoTeXscout.io/api",
              browserURL: "https://testnet.IoTeXscan.io"
            }
          }
        ],
      },
    ```
3.  **Verify the Contract:** Execute the following command, replacing `<address>` with your contract's address:

    ```css
    npx hardhat verify --network testnet YOUR_CONTRACT_ADDRESS
    ```


4. Upon successful execution, you'll receive a link to your contract's verified code on IoTeXscan.
