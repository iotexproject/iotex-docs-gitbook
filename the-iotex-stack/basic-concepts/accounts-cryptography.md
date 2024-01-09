# Accounts cryptography

## Private Key

In IoTeX, the accounts Private Key is generated as 64 random hex characters, e.g.:

`90bf89cd944df5c6d8281b132783277c1760537809c534fc54dda34c4edfb4f4`

And the corresponding **Public Key** is derived from the private key using ECDSA with the secp256k1 curve, which is the same as Ethereum.

{% hint style="success" %}
Given a signed message, you can recover the public key of the signing account using [Ecrecover](https://github.com/ethereum/go-ethereum/blob/master/crypto/signature\_cgo.go#L36), also defined in [solidity](https://docs.soliditylang.org/en/latest/solidity-by-example.html?highlight=ecrecover#recovering-the-message-signer-in-solidity) for signature verification in smart contracts.
{% endhint %}

## Address Construction

An IoTeX native representation of an account address like:

&#x20;`io1nyjs526mnqcsx4twa7nptkg08eclsw5c2dywp4`&#x20;

can be constructed using the following steps:

#### 1. Generate a random private key as 64 random hex characters

`privKey =`&#x20;

`0700898c9dcae0279c88318003ee210e1ee2514121d292d2f03739498ce95f4e`

#### 2. Calculate the corresponding public key using secp256k1 elliptic curve

`pubKey := keccak256k1(privKey) =`&#x20;

`046748ee7f4b573f1fb17517005499003385da75788b2052b18bbb05fd0dcf50597ffc54a22a02ca7343ed2654212022c1f4a0c3755dbdb81a2e70c7c0805520dc`

#### 3. Apply `keccak256` hash function to the public key, excluding the first byte

`hash := keccak256(pubKey[1:]) =`

`42a1c0796606183ccdb3d935147e805c858840099190e208d7a04a74f2a0aac8`

#### 4. Take the last 20 bytes of the hash

`payload := hash[12:] =`

`147e805c858840099190e208d7a04a74f2a0aac8`

this is the "byte representation" of the address

#### 5. Convert the byte representation to 5-bit encoding (base32)

2, 17, 31, 8, 0, 23, 4, 5, 17, 1, 0, 0, 19, 4, 12, 16, 28, 8, 4, 13, 15, 8, 2, 10, 14, 19, 25, 10, 1, 10, 22, 8

See a go lang implementation for the [5-bit conversion](https://github.com/iotexproject/iotex-address/blob/b07b71fc7866257680b75f1ab9c79c95dc6d255b/address/bech32/bech32.go#L141) implementation or a [nodejs](https://www.npmjs.com/package/bech32) package (use `toWords()` to convert a bytes array into 5-bit words).

#### 6. Apply the [bech32 ](https://github.com/bitcoin/bips/blob/master/bip-0173.mediawiki)encoding on the 5-bit payload with the `io` prefix

`address :=`

`io1bc1qz3lgqhy93pqqnyvsugyd0gz2wne2p2kght0g4r`

See a go lang implementation for the [bech32 encoding](https://github.com/iotexproject/iotex-address/blob/b07b71fc7866257680b75f1ab9c79c95dc6d255b/address/bech32/bech32.go#L97) implementation or a [nodejs](https://www.npmjs.com/package/bech32) package (use `encode` to encode 5-bit words with a prefix).
