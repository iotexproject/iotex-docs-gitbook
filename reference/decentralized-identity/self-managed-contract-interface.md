# Self-Managed Contract Interface

Our DID design allows each manufacture or entity to have its own namespace, which stores and manages DIDs through a self-managed DID contract. A self-managed contract could have customized business logic to adapt the application's needs but has to implement the **SelfManagedDID** interface, defined as follows:

```javascript
interface SelfManagedDID {
    function createDID(string id, bytes32 hash, string uri) public returns (string);
    function deleteDID(string did) public;
    function updateHash(string did, bytes32 hash) public;
    function updateURI(string did, string uri) public;
    function getHash(string did) public view returns (bytes32);
    function getURI(string did) public view returns (string);
}
```

The following part of this document specifies the IoTeX implementation of the SelfManagedDID interface with [DID Method](https://w3c-ccg.github.io/did-spec/#specific-did-method-schemes) `[did:io]`.

### Method Name

We use the `iotex` to be our method name and a formal DID using this method need begin with following prefix: `did:io` . Furthermore, all the characters in the prefix need to be in lowercase. The string after prefix is the unique IoTeX account address of the registered user/device.

### Generate a unique ID string <a id="generate-a-unique-id-string"></a>

Every user or device needs to register its own DID by uploading its UUID under a namespace, DID document hash, and DID document URI. Then a unique `idstring` is created as follows:

1. Construct the `iotex` method prefix, i.e. `did:io`.
2. Append the UUID \(IoTeX account address\) to the prefix. The UUID must match caller's address.
3. The provided DID document hash and URI would be stored in the contract along the unique `idstring`.

The DID structure looks like follows:

```c
struct DID {
        bool exist;
        bytes32 hash;
        string uri;
}
```

### Example

An example IoTeX DID:

```javascript
did:io:0x5576E95935366Ebd2637D9171E4C92e60598be10
```

