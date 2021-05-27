# Update a IoTeX DID

Whenever a DID document is modified, the document hash will change and need to be updated in the DID contract. If a user moves the document to a new storage location, the document URI also needs to be updated in the DID contract. Every device can only update its own document associated with the DID created by itself. Here is a draft DID hash/URI update implementation:

```javascript
// For reference only and subject to change

modifier onlyDIDOwner(string didInput) {
    string memory didString = generateDIDString();
    if (bytes(didInput).length > 0) {
        require(compareStrings(didInput, didString), "caller does not own the given did");
    }
    require(dids[didString].exist, "caller is not a did owner");
    _;
}

function updateHash(string did, bytes32 hash) public onlyDIDOwner(did) {
    dids[generateDIDString()].hash = hash;
}

function updateURI(string did, string uri) public onlyDIDOwner(did) {
    dids[generateDIDString()].uri = uri;
}

```

Similar to the case of DID registration, did argument is optional for the update functions as well because the contract would use caller's address to derive the DID string.

