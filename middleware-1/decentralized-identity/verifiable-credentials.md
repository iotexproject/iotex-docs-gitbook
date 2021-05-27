# Verifiable Credentials

Verifiable claims are statements made by an entity about a 'subject' whose authorship can be cryptographically verified. They can be combined with DID documents to provide trusted service. IoTeX verifiable credentials include the following features:

* Claims are used to create **verifiable credentials** by issuers.
* Verifiable credentials are **decentralized** and **contextual**.
* Credential issuers decide on which claims are contained in the credentials.
* Verifiers **make their own trust decisions** about which credentials to accept.
* Verifiers do not need to contact issuers to perform verification.
* Credential holders are free to choose which credentials to carry and what information to disclose.

Here is a draft IoTeX verifiable credentials example:

```javascript
{
    "@context": "https://w3id.org/credentials/v1",
    "id": "did:io:0xb36A1D1778f9D5E5816682c2cC0d16C65828a6b4/credentials/1",
    "type": ["Credential", "NameCredential"],
    "issuer": "did:io:0x669d00D4191fB397c780212EB81B439F5Ec9967d",
    "issued": "2019-09-01",
    "claim": {
        "id": "did:io:0x669d00D4191fB397c780212EB81B439F5Ec9967d",
        "name": "John Doe",
        "address": "..."
    },
    "proof": {
        "type": "RsaSignature2018",
        "created": "2017-06-18T21:19:10Z",
        "creator": "did:io:0xb36A1D1778f9D5E5816682c2cC0d16C65828a6b4#key-1",
        "nonce": "c0ae1c8e-c7e7-469f-b252-86e6a0e7387e",
        "signatureValue": "BavEll0/I1zpYw8XNi1bgVg/sCneO4Jugez
         8RwDg/+MCRVpjOboDoe4SxxKjkCOvKiCHGDvc4krqi6Z1n0
         UfqzxGfmatCuFibcC1wpsPRdW+gGsutPTLzvueMWmFhw
         YmfIFpbBu95t501+rSLHIEuujM/+PXr9Cky6Ed+W3JT24=
    }
}
```

