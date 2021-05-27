# Create/Register a IoTeX DID

IoTeX DID contract implements the functionality of DID registrations. It associates every IoTeX account with a unique decentralized identifier and a corresponding DID document. Every IoTeX account can only register one DID for itself. It is required that the registerer provides the DID document URI where its document can be accessed and the current document hash that represents the initial state of the document. Here is a draft DID registry implementation:

```typescript
// For reference only and subject to change

string constant didPrefix = "did:io:";
struct DID {
    bool exist;
    bytes32 hash;
    string uri;
}
mapping(string => DID) dids;

function createDID(string id, bytes32 hash, string uri) public returns (string) {
    if (bytes(id).length > 0) {
        require(compareStrings(id, addrToString(msg.sender)), "id does not match creator");
    }
    string memory resultDID = generateDIDString();
    require(!dids[resultDID].exist, "did already exists");
    dids[resultDID] = DID(true, hash, uri);
    return resultDID;
}

function generateDIDString() private view returns (string) {
    return string(abi.encodePacked(didPrefix, addrToString(msg.sender)));
}
```

An example of registration:

```javascript
createDID("0x5576E95935366Ebd2637D9171E4C92e60598be10", "8806157fdcbcea265623576fa72d88568db3f9ca8b36bddfe3755ae80457eaf5", "user:password@tcp(example_connection_string:3306)/")
```

Note that id argument is optional because the contract will use the caller's address anyway. Once a DID is registered, the provided DID document hash and URI would be stored in the contract along the unique DID string.

