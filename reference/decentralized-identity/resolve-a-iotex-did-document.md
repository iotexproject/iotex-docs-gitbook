# Resolve a IoTeX DID Document



IoTeX DID document is a JSON-LD document containing six, optional components:

* The DID that points to the DID Document, identified by the key **id**
* A list of public keys identified by the key **publickey**
* List of protocols for authentication control of the DID and delegated capabilities identified by the key **authentication**
* A set of service endpoints that allow discovery of way to interact with the entity, identified by the key **service**
* A timestamp indicates when the DID Document was created and updated, identified by the key **created/updated**
* A digital signature for verifying the integrity of DID Document, identified by the key **proof**

{% hint style="success" %}
IoTeX DID has been integrated by [uniresolver.io \(opens new window\)](http://uniresolver.io/)which is the industrial de facto that resolves DID to the corresponding document
{% endhint %}

Here is a draft IoTeX DID document example:

```javascript
{
  "@context": "https://w3id.org/did/v1",
  "id": "did:io:0x88C36867cffB66197812a9385A038cc6Dd75244b",
  "publicKey": [
    {
      "id": "did:io:0x5576E95935366Ebd2637D9171E4C92e60598be10#keys-1",
      "type": "RsaVerificationKey2018",
      "controller": "did:io:0x56d0B5eD3D525332F00C9BC938f93598ab16AAA7",
      "publicKeyPem": "-----BEGIN PUBLIC KEY...END PUBLIC KEY-----\r\n"
    }
  ],
  "authentication": [
    {
      "type": "RsaSignatureAuthentication2018",
      "publicKey": "did:io:0x5576E95935366Ebd2637D9171E4C92e60598be10#keys-1"
    }
  ],
  "service": [
    {
      "id": "did:io:0x88C36867cffB66197812a9385A038cc6Dd75244b;exam_svc",
      "type": "ExampleService",
      "serviceEndpoint": "https://example.com/endpoint/8377464"
    }
  ],
  "created": "2018-02-08T16:03:00Z",
  "proof": {
    "type": "LinkedDataSignature2015",
    "created": "2018-02-08T16:02:20Z",
    "creator": "did:io:0x5576E95935366Ebd2637D9171E4C92e60598be10#keys-1",
    "signatureValue": "QNB13Y7Q9...1tzjn4w=="
  }
}
```

