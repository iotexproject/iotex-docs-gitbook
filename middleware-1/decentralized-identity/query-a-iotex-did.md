# Query a IoTeX DID

IoTeX clients can query a DID's current hash and URI given a DID string whether they own the DID or not. Here is a draft DID hash/URI read implementation:

```javascript
// For reference only and subject to change

function getHash(string did) public view returns (bytes32) {
    require(dids[did].exist, "did does not exist");
    return dids[did].hash;
}

function getURI(string did) public view returns (string) {
    require(dids[did].exist, "did does not exist");
    return dids[did].uri;
}
```



