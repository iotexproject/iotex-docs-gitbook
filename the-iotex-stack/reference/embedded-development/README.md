# Embedded Development

## Overview

The blockchain client SDK is targeted to embedded devices and allows you to easily interact with the IoTeX blockchain in order to fetch blockchain data, send transactions or perform contract execution actions.

## How does it work

The communication with the blockchain is done over HTTP**,** using the HTTP to JSON-RPC bridge at **gateway.iotexlab.io.**

## Supported devices

* Unix machines with curl support
* ESP32 based boards using Arduino framework
* ESP8266 based boards using Arduino framework
* Nano33 IoT using Arduino framework
* Arduino MKR WiFi 1010 using Arduino framework (not tested)

## Porting to a new platform

Effort has been taken in trying to decouple non-platform dependant code as much as possible. However, a specific implementation of the following modules is needed when porting the library to a non supported device:

* **Http**: the HTTP interface needs implemented. See `src/http/platform_name/http.cpp` for implemented platforms.
* **Storage**: The storage class needs implemented. It contains only two methods: `savePrivateKey()` saves the private key, and `readPrivateKey()` reads the private key. See `src/storage/platform_name/storage.cpp` for implemented platforms.
* **Random**: The random class needs implemented for true random number generation. It contains a single method `fillRandom()`, that fills a buffer with random bytes. See `src/random/platform_name/random.cpp` for implemented platforms.

## Library architecture

Below are the main modules comprising the SDK:

<details>

<summary>ABI</summary>

Classes and functions to encode data using the Ethereum abi specification.

</details>

<details>

<summary>Account</summary>

Classes and functions to create a wallet from a private key, obtain the address and send actions to the blockchain.

</details>

<details>

<summary>API</summary>

Classes and functions that wrap the HTTP endpoint calls to interact with the blockchain.

</details>

<details>

<summary>Connection</summary>

Classes and methods that represent a connection to the blockchain.

</details>

<details>

<summary>Contract</summary>

Classes and methods to interact with contracts.

</details>

<details>

<summary>Encoder</summary>

Classes and methods to perform different types of encoding (eg. bech32, protobuf, base64).

</details>

<details>

<summary>HTTP</summary>

Classes and methods to perform HTTP requests.

</details>

<details>

<summary>Protobuf</summary>

Classes and methods to handle protobuf message serialization and deserialization.

</details>

<details>

<summary>Random</summary>

Random generator implementations for each platform.

</details>

<details>

<summary>Signer</summary>

Classes and functions to sign messages.

</details>

<details>

<summary>Storage</summary>

Classes and functions to store and read the private key from persistent storage.

</details>

