# Owned Accounts

For owned accounts, the private key is used to _sign_ actions on behalf of the account itself: because each and every account address has one and only one associated private key, we can say that any blockchain action signed by a certain address _is owned_ by whoever know the private key that generates that address.

While the address of an account can be generated from the private key, the opposite is not possible: no one can trace the private key that generated a certain address from the knowledge of the address alone. For this reason, the address can be safely shared with anyone \(e.g. to receive transfers\) while the private key should always be kept secret and safely stored as it's used to _control_ the account, and it represents the proof of ownership of that account and all the actions it initiated.

