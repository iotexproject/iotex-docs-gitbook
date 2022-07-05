# W3bStream SDK

The client application is wrapped as an SDK that should be integrated with Web2 IoT partners’ applications and serve as the bridge to connect a Web2-based IoT system to the W3bStream node(s). \
\
The client application SDK contains the following functions:

* `keyGen()` – Generate a secp256k1 ECC private and public key pair
* `twinIdGen(pubKey)` – Derive a decentralized identifier (DID) for the device’s digital twin from the public key
* `ecdsaSign(msg, len, priKey)` – Generate an ECDSA signature on a message of length len
* `devBind(devId, twinId, walletAddr, ownerSig)` – Bind an IoT device identity (i.e., device identifier devID and its digital twin identifier twinID) with its owner’s blockchain wallet address
* `dataEncode(dataRaw, dataObj, algorithmId)` – Encode the raw data into a data object using a specific data encoding algorithm
* `dataEncrypt(dataObj, encObj)` – Encrypt a data object with AES encryption
* `dataSend(devId, dataObj, protocolId, endPoint)` – Send a data object to a connectivity endpoint
