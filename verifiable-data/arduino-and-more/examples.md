# Examples

## GetAccountMetadata()

Gets the account details for an IoTeX address

```
AccountMeta accountMeta;
ResultCode result = connection.api.wallets.getAccount("io1xkx7y9ygsa3dlmvzzyvv8zm6hd6rmskh4dawyu", accountMeta);
```

If result is `SUCCESS` then the account metadata is be stored in `accountMeta` The account metadata contains the following fields:

* address: the IoTeX address
* balance: the balance in RAU
* nonce: the account nonce
* pendingNonce: the account's pending nonce
* isContract: true if the address is a contract



## GetTransactionByHash()

Gets the data for a transfer given the transaction hash

```
ActionInfo_Transfer data;
    ResultCode result = connection.api.wallets.getTransactionByHash("5444318f1a460c74d3e86918b640272d93d0b30e2bf2dc329dfd3faa636e52ec", data);
```

If result is `SUCCESS` then the action data is stored in `data`. The  transfer action data contains the following fields:



* actHash
* blkHash
* timestamp
* blkHeight
* sender
* gasFee
* action
  * senderPublicKey
  * signature
  * core
    * version
    * nonce
    * gasLimit
    * gasPrice
    * execution
      * amount
      * contract
      * data



## Creating an account

We can create an account in the device from an existing private key, or generating a new private key

### From an existing private key

```
const char pkString[] = <private_key>;

// Convert the privte key hex string byte array
uint8_t pkBytes[IOTEX_PRIVATE_KEY_SIZE];
signer.str2hex(pkString, pkBytes, IOTEX_SIGNATURE_SIZE);

Account account(pkBytes);
```

### Generating a new private key

```
// Generate a random private key
uint8_t pkBytes[IOTEX_PRIVATE_KEY_SIZE];
randomGenerator.fillRandom(pkBytes, sizeof(pkBytes));

// Create the account 
Account account(pkBytes);
```

### Getting the details of the account

Now that the account is created, you can get the address in Ethereum or IoTeX format, and the public/private keys:

```
// Create buffers for the account details
char publicKeyBuf[IOTEX_PUBLIC_KEY_C_STRING_SIZE] = {0};
char privateKeyBuf[IOTEX_PRIVATE_KEY_C_STRING_SIZE] = {0};
char ethAddressBuf[ETH_ADDRESS_C_STRING_SIZE] = {0};
char ioAddressBuf[IOTEX_ADDRESS_C_STRING_SIZE] = {0};

// Get the account details (ad hexadecimal strings)
account.getPublicKeyString(publicKeyBuf);
account.getPrivateKeyString(privateKeyBuf);
account.getEthereumAddress(ethAddressBuf);
account.getIotexAddress(ioAddressBuf);
```

## Sending a transfer of IOTX

Sends a transfer of IOTX tokens

First create the account object:

```
// Private key of the origin address
const char pkString[] = <private_key>;

// Recipient IoTeX address
char destinationAddr[IOTEX_ADDRESS_C_STRING_SIZE] = <destination_address>;

// Convert the private key and address hex strings to byte arrays
uint8_t pkBytes[IOTEX_PRIVATE_KEY_SIZE];
signer.str2hex(pkString, pkBytes, IOTEX_SIGNATURE_SIZE);

// Create the account object
Account originAccount(pkBytes);

// Get the IoTeX address
char originIotexAddr[IOTEX_ADDRESS_C_STRING_SIZE] = "";
originAccount.getIotexAddress(originIotexAddr);
```

Then query the blockchain to get the account nonce:

```
AccountMeta accMeta;
ResultCode result = connection.api.wallets.getAccount(originIotexAddr, accMeta);
IotexString nonceString = accMeta.pendingNonce;
uint64_t nonce = atoi(nonceString.c_str());
```

Now broadcast the transfer with the retrieved nonce:

```
// Amount of RAU to transfer. Eg: 1 RAU
char amount[IOTEX_ADDRESS_C_STRING_SIZE] = "1";

// Send the transfer 
uint8_t hash[IOTEX_HASH_SIZE] = {0};
result = originAccount.sendTokenTransferAction(connection, nonce, 20000000, "1000000000000", amount, destinationAddr, hash);
```

## Signing a message

Signs a message

First convert the private key to a byte array:

```
const char pkString[] = <private_key>;
uint8_t pkBytes[IOTEX_PRIVATE_KEY_SIZE];
signer.str2hex(pkString, pkBytes, IOTEX_SIGNATURE_SIZE);
```

Now sign the message

```
// Message to sign as a byte array
const uint8_t message[] = { 0xab, 0xcd };
uint8_t signature[IOTEX_SIGNATURE_SIZE] = {0};
signer.signMessage(message, sizeof(message), pkBytes, signature);
```

The signature is stored as a byte array in `signature`

## Storing the private key to persistent memory in the device

You can store the private key in the EEPROM or flash memory of your Arduino device, or in a text file in Linux

First convert the private key to a byte array:

```
const char pkString[] = <private_key>;
uint8_t pkBytes[IOTEX_PRIVATE_KEY_SIZE];
signer.str2hex(pkString, pkBytes, IOTEX_SIGNATURE_SIZE);
```

First initialize the storage module (not needed for Nano33 IoT or Linux):

```
// The number of bytes we want to use for the EEPROM
// This is passed to EEPROM.begin()
// Should be at least IOTEX_PRIVATE_KEY_SIZE
uint32_t eepromSize = IOTEX_PRIVATE_KEY_SIZE;
storage.Initialize(eepromSize);
```

Now store the private key:

```
// Specify any address number between 0 and (eepromSize - IOTEX_PRIVATE_KEY_SIZE). 
// This is the EEPROM address where the private key is stored. There needs to be suficcient space between eepromAddress and eepromSize to store the whole private key (at least IOTEX_PRIVATE_KEY_SIZE bytes)
const uint32_t eepromAddress = 0;
ResultCode result = storage.savePrivateKey(eepromAddress, pkBytes);
```

You can also read the private key that is stored in the device:

```
result = storage.readPrivateKey(eepromAddress, pkBytes);
```

## Sending a XRC20 token transfer

First convert the private key to a byte array:

```
const char pkString[] = <private_key>;
uint8_t pkBytes[IOTEX_PRIVATE_KEY_SIZE];
signer.str2hex(pkString, pkBytes, IOTEX_SIGNATURE_SIZE);
```

Also convert the destinationn address to a byte array:

```
const char destAddrString[] = "0x5840bf8e5d3f5b66EE52B9b933bDAC9682E386D0";
uint8_t destAddrBytes[ETH_ADDRESS_SIZE];
signer.str2hex(destAddrString, destAddrBytes, ETH_ADDRESS_SIZE);
```

Generate the contract call data:

```
// Amount to transfer
uint64_t value = 1000000000000000000;
uint8_t data[IOTEX_CONTRACT_ENCODED_TRANSFER_SIZE] = {0};
Xrc20Contract::generateCallDataForTransfer(destAddrBytes, value, data);
char callData[IOTEX_CONTRACT_ENCODED_TRANSFER_SIZE * 2 + 1] = {0};
signer.hex2str(data, IOTEX_CONTRACT_ENCODED_TRANSFER_SIZE, callData, sizeof(callData));
```

Create the account object and get the account metadata in order to obtain the nonce:

```
Account originAccount(pkBytes);
AccountMeta accMeta;
char originIotexAddr[IOTEX_ADDRESS_STRLEN] = {0};
originAccount.getIotexAddress(originIotexAddr);
connection.api.wallets.getAccount(originIotexAddr, accMeta);
int nonce = atoi(accMeta.pendingNonce.c_str());
```

Broadcast the XRC20 token transfer

```
// The token address. Eg: VITA token
const char tokenAddress[] = "io1hp6y4eqr90j7tmul4w2wa8pm7wx462hq0mg4tw";
uint8_t hash[IOTEX_HASH_SIZE] = {0};
ResultCode result = originAccount.sendExecutionAction(connection, atoi(accMeta.pendingNonce.c_str()), 20000000, "1000000000000", "0", tokenAddress, callData, hash);
```



## Calling a contract function

This example shows how to call a contract funcion using the addData function of the contract **io1n49gavyahsukdvvxxandkxephdx93n3atcrqur** as an example. You can find the contract abi at https://github.com/iotexproject/arduino-sdk/blob/main/examples/ContractAddData/addDataAbi.h

First convert the private key to a byte array:

```
const char pkString[] = <private_key>;
uint8_t pkBytes[IOTEX_PRIVATE_KEY_SIZE];
signer.str2hex(pkString, pkBytes, IOTEX_SIGNATURE_SIZE);
```

Create the account object and get the account metadata in order to obtain the nonce:

```
Account originAccount(pk);
AccountMeta accMeta;
char originIotexAddr[IOTEX_ADDRESS_C_STRING_SIZE] = "";
originAccount.getIotexAddress(originIotexAddr);
ResultCode result = connection.api.wallets.getAccount(originIotexAddr, accMeta);
int nonce = atoi(accMeta.pendingNonce.c_str());
```

Create the function call parameters:

```
ParameterValue paramImei = MakeParamString(imei);
ParameterValue paramData = MakeParamBytes(data, sizeof(data), true);
ParameterValue paramSig = MakeParamBytes(signature, sizeof(signature), true);
```

Create the dictionary that contain the parameters and their values:

```
ParameterValuesDictionary params;
params.AddParameter("imei", paramImei);
params.AddParameter("data", paramData);
params.AddParameter("signature", paramSig);
```

Create the contract object:

```
// The contract abi as a serialized json string
String abi = <contract_abi_json_string>;
Contract contract(abi);
```

Generate the call data:

```
String callData = "";
contract.generateCallData("addData", params, callData);
```

Broadcast the contract execution action

```
uint8_t hash[IOTEX_HASH_SIZE] = {0};
result = originAccount.sendExecutionAction(connection, nonce, 20000000, "1000000000000", "0", contractAddress, callData, hash);
```
