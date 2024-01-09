# IoTeX Wallet HD Derivation Path

{% hint style="info" %}
This page is intended for developers and people who would like to deep dive in IoTeX wallet knowledge. Please be careful if you extract private keys manually.
{% endhint %}

HD derivation path means hierarchical deterministic wallet derivation path. It is a way to derive multiple accounts from the same mnemonic seed.&#x20;

IoTeX uses `m/44'/304` as its HD path. You can view all HD paths for all coins here: [https://github.com/satoshilabs/slips/blob/master/slip-0044.md](https://github.com/satoshilabs/slips/blob/master/slip-0044.md)

If you use mnemonic seed and HD to derive wallets, `m/44'/304'/0'/0` is the 0-th wallet for IoTeX Wallet and `m/44'/304'/0'/1` is the 1st wallet.&#x20;

A full HD path is usually like this

```
m / purpose' / coin_type' / account' / change / address_index
```

Using this HD path, you can manually derive your private keys from mnemonic seed. A tool you can do that is [https://iancoleman.io/bip39/](https://iancoleman.io/bip39/).&#x20;

{% hint style="warning" %}
Any online tools are not safe if you operate your mnemonic seed or private keys. If download the tool and run it locally. Please also use an offline computer to run it.
{% endhint %}

A tutorial of using the tool with IoTeX wallet is [https://community.iotex.io/t/migrate-your-iotex-wallet-from-trust-wallet-to-iopay/2352](https://community.iotex.io/t/migrate-your-iotex-wallet-from-trust-wallet-to-iopay/2352)
