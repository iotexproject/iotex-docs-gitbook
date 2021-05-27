# Accounts cryptography

## Private Key

In IoTeX, the accounts Private Key is generated as a 64 random hex characters, e.g.:

`90bf89cd944df5c6d8281b132783277c1760537809c534fc54dda34c4edfb4f4`

and the corresponding **Public Key** is derived from the private key using ECDSA \(secp256k1\), which is exactly the same as Ethereum.

{% hint style="success" %}
Given a signed message, you can recover the public key of the signing account using [this function ](https://github.com/ethereum/go-ethereum/blob/master/crypto/signature_cgo.go#L36)
{% endhint %}

## Address Construction

A IoTeX human readable address like `io1nyjs526mnqcsx4twa7nptkg08eclsw5c2dywp4` can be constructed using the following steps:

1. Generate a random private key as a 64 random hex characters
2. Calculate the corresponding public key using secp256k1 elliptic curve
3. Apply `keccak256` hash function to the public key, excluding the first byte: `hash := keccak256(pk[1:])`
4. Take the last 20 bytes of the hash as the payload: `payload := hash[12:]` , this is the byte representation of the address
5. Apply the [bech32 ](https://github.com/bitcoin/bips/blob/master/bip-0173.mediawiki)encoding on the payload, and add the `io1` prefix.

