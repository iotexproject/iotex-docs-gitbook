# Delete a IoTeX DID

A registered DID can be deactivated anytime as long as the caller's address matches the address within the DID string. Once a DID is deactivated, the metadata of the corresponding document cannot be updated. Here is a draft DID hash/URI delete implementation:

```
// For reference only and subject to change

function deleteDID(string did) public onlyDIDOwner(did) {
    dids[generateDIDString()].exist = false;
}
```

Similar to previous cases, the contract checks the permission to ensure that only the DID creator can deactivate its own DID.
