# Table of contents

* [Welcome](README.md)

## 🛠Get Started

* [IoTeX Wallets](get-started/iotex-wallets/README.md)
  * [Official ioPay Wallet](get-started/iotex-wallets/official-iopay-wallet.md)
  * [Metamask Wallet](get-started/iotex-wallets/metamask.md)
  * [Command line client](get-started/iotex-wallets/command-line-client/README.md)
    * [Install ioctl cli](get-started/iotex-wallets/command-line-client/install-ioctl-cli.md)
    * [Create wallet account](get-started/iotex-wallets/command-line-client/create-an-iotex-account.md)
    * [Interact with the blockchain](get-started/iotex-wallets/command-line-client/interact-with-the-blockchain.md)
* [Obtain Test Tokens](get-started/iotx-faucets.md)
* [IoTeX dApp Starter](get-started/iotex-dapp-starter.md)

## dApp Development

---

* [Ethereum Development](ethereum-copmpatibility/README.md)
  * [Web3.js](ethereum-copmpatibility/web3.js.md)
  * [Remix](ethereum-copmpatibility/remix.md)
  * [Truffle](ethereum-copmpatibility/truffle.md)
  * [Hardhat](ethereum-copmpatibility/hardhat.md)
  * [Subgraph](ethereum-copmpatibility/subgraph.md)
* [Native Development](iotex-antenna-sdk/README.md)
  * [Overview](iotex-antenna-sdk/antenna-overview.md)
  * [Configure a local IoTeX Testnet](iotex-antenna-sdk/install-a-local-testnet.md)
  * [Import Antenna SDK](iotex-antenna-sdk/antenna-installation/README.md)
    * [Antenna JS](iotex-antenna-sdk/antenna-installation/install-antenna-js.md)
    * [Antenna Go](iotex-antenna-sdk/antenna-installation/antenna-go.md)
    * [Antenna Swift](iotex-antenna-sdk/antenna-installation/antenna-swift.md)
    * [Antenna Java](iotex-antenna-sdk/antenna-installation/antenna-java.md)
    * [Antenna Embedded](iotex-antenna-sdk/antenna-installation/antenna-embedded.md)
  * [Example code](iotex-antenna-sdk/reference-code/README.md)
    * [Create an account](iotex-antenna-sdk/reference-code/create-an-account.md)
    * [Make Token Transfers](iotex-antenna-sdk/reference-code/make-token-transfers.md)
    * [XRC20 Tokens](iotex-antenna-sdk/reference-code/xrc20-tokens.md)
    * [Interact with smart contracts](iotex-antenna-sdk/reference-code/interact-with-smart-contracts.md)
    * [Interact with ioPay Desktop](iotex-antenna-sdk/reference-code/interact-with-iopay-desktop.md)
    * [Create a DID JWT](iotex-antenna-sdk/reference-code/create-a-did-jwt.md)
    * [Call any RPC method](iotex-antenna-sdk/reference-code/call-any-rpc-method.md)
* [Tutorials](smart-contracts/README.md)
  * [Deploy an XRC20 Token](smart-contracts/introduction/README.md)
    * [Deploy Using Remix](smart-contracts/introduction/deploy-using-remix.md)
    * [Deploy using IoTeX Studio](smart-contracts/introduction/issue-xrc20-tokens-on-iotex.md)
    * [Submit Token Metadata](smart-contracts/introduction/token-metadata.md)

## 🧑‍💻Middleware <a id="middleware-1"></a>

* [Decentralized Identity](middleware-1/decentralized-identity/README.md)
  * [Overview](middleware-1/decentralized-identity/overview.md)
  * [Self-Managed Contract Interface](middleware-1/decentralized-identity/self-managed-contract-interface.md)
  * [Create/Register a IoTeX DID](middleware-1/decentralized-identity/create-register-a-iotex-did.md)
  * [Query a IoTeX DID](middleware-1/decentralized-identity/query-a-iotex-did.md)
  * [Update a IoTeX DID](middleware-1/decentralized-identity/update-a-iotex-did.md)
  * [Delete a IoTeX DID](middleware-1/decentralized-identity/delete-a-iotex-did.md)
  * [Resolve a IoTeX DID Document](middleware-1/decentralized-identity/resolve-a-iotex-did-document.md)
  * [Verifiable Credentials](middleware-1/decentralized-identity/verifiable-credentials.md)
  * [Security Considerations](middleware-1/decentralized-identity/security-considerations.md)
  * [References](middleware-1/decentralized-identity/references.md)

## 🔐Secure Hardware

* [Pebble Tracker](secure-hardware/pebble-tracker/README.md)
  * [Overview](secure-hardware/pebble-tracker/overview.md)
  * [Quick Start](secure-hardware/pebble-tracker/quick-start.md)
  * [Technical Specification](secure-hardware/pebble-tracker/technical-specification.md)
  * [Hardware Setup](secure-hardware/pebble-tracker/hardware-setup.md)
  * [Setup modes](secure-hardware/pebble-tracker/setup-modes/README.md)
    * [Development mode](secure-hardware/pebble-tracker/setup-modes/development-mode/README.md)
      * [Deploy the backend service](secure-hardware/pebble-tracker/setup-modes/development-mode/deploy-the-backend-service.md)
      * [Send data to the backend](secure-hardware/pebble-tracker/setup-modes/development-mode/send-data-to-the-backend.md)
    * [Production mode](secure-hardware/pebble-tracker/setup-modes/production-mode/README.md)
      * [Configure AWS IoT Core](secure-hardware/pebble-tracker/setup-modes/production-mode/configure-aws-iot-core.md)
      * [Send data to AWS IoT Core](secure-hardware/pebble-tracker/setup-modes/production-mode/send-data-to-aws-iot-core.md)
  * [Develop and Build the Firmware](secure-hardware/pebble-tracker/develop-and-build-the-firmware/README.md)
    * [Build on Windows](secure-hardware/pebble-tracker/develop-and-build-the-firmware/build-on-windows.md)
    * [Build on Linux/macOS](secure-hardware/pebble-tracker/develop-and-build-the-firmware/build-on-linux-macos.md)
    * [Configure the firmware](secure-hardware/pebble-tracker/develop-and-build-the-firmware/configure-the-firmware.md)
  * [Flashing the firmware](secure-hardware/pebble-tracker/flashing-the-firmware/README.md)
    * [Application firmware](secure-hardware/pebble-tracker/flashing-the-firmware/application-firmware.md)
    * [Bootloader firmware](secure-hardware/pebble-tracker/flashing-the-firmware/bootloader-firmware.md)

## 📕Reference

* [Babel - Web3 API](reference/babel-web3-api.md)
* [iotex-core - gRPC API](reference/node-core-api-grpc.md)
* [Analytics - GraphQL API](reference/analytics.md)
* [ioctl cli - Reference](reference/ioctl-cli-reference/README.md)
  * [Installation](reference/ioctl-cli-reference/installation.md)
  * [Accounts](reference/ioctl-cli-reference/accounts.md)
  * [HD Wallet Account](reference/ioctl-cli-reference/hd-wallet-account.md)
  * [Aliases](reference/ioctl-cli-reference/aliases.md)
  * [Send Actions](reference/ioctl-cli-reference/send-actions.md)
  * [Query the Blockchain](reference/ioctl-cli-reference/query-the-blockchain.md)
  * [Smart Contracts](reference/ioctl-cli-reference/smart-contracts.md)
  * [Staking & Voting](reference/ioctl-cli-reference/staking-and-voting.md)
  * [XRC20 Tokens](reference/ioctl-cli-reference/xrc20-tokens.md)
  * [Decentralized Identity](reference/ioctl-cli-reference/decentralized-identity.md)
  * [JWT Tokens](reference/ioctl-cli-reference/jwt-tokens.md)

## ⚙️MORE RESOURCES

* [Clone Existing Projects](more-resources/clone-existing-projects/README.md)
  * [Rolling Dice](more-resources/clone-existing-projects/rolling-dice.md)
  * [Automatic rewards distrubution](more-resources/clone-existing-projects/automatic-rewards-distrubution.md)
* [Exchange Integration](more-resources/exchange-integration/README.md)
  * [General Guide](more-resources/exchange-integration/general-guide.md)
  * [Rosetta API](more-resources/exchange-integration/rosetta-api.md)
* [Action Injector](more-resources/misc-tools.md)
* [Rewards distribution](more-resources/rewards-distribution/README.md)
  * [Hermes](more-resources/rewards-distribution/hermes.md)
  * [Analytics Bookkeeping](more-resources/rewards-distribution/analytics-bookkeeping.md)

## 💡Basic Concepts

* [Wallet Accounts](basic-concepts/accounts.md)
* [Accounts cryptography](basic-concepts/accounts-cryptography.md)
* [Blockchain Actions](basic-concepts/blockchain-actions.md)
* [Address Conversion](basic-concepts/address-conversion.md)
* [Blockchain Nodes](basic-concepts/blockchain-nodes.md)
* [IOTX Token](basic-concepts/iotx-token.md)
* [Chain ID](basic-concepts/chain-id.md)

