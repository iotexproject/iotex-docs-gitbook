# HD Wallet Account

### Create the HD Wallet

Create the HD Wallet and provide the mnemonic phrase.

`Usage: ioctl hdwallet create`

**Example**

```aspnet
➜ ioctl hdwallet create
Set password
# Enter a password to access this account
Enter password again
# Repeat your password
Mnemonic phrase: object gentle entry place cigar minimum crowd lounge collect tray describe brush
It is used to recover your wallet in case you forgot the password. Write them down and store it in a safe place.
```

### Delete the HD Wallet

Deletes the HD Wallet from the system

`Usage: ioctl hdwallet delete`

**#Example**

```
➜ ioctl hdwallet delete
** This is an irreversible action!
Once an hdwallet is deleted, all the assets under this hdwallet may be lost!
Type 'YES' to continue, quit for anything else.
Options: yes
Quit for anything else.
# Type yes to delete or Ctrl+C to cancel

```

### Derive an address <a href="#derive-an-address-of-the-hd-wallet" id="derive-an-address-of-the-hd-wallet"></a>

Derive an address from the HD Wallet given a certain derivation path.

`Usage: ioctl hdwallet derive id1/id2/id3`

**Example**

```
➜ ioctl hdwallet derive 44/60/0
Enter password
# Type your HW Wallet password here

address: io19tuxh388pnxuacmtplrr5t207t6mqwxzcjp296

```

## Send transactions <a href="#export-the-hd-wallet" id="export-the-hd-wallet"></a>

Once you imported a seed phrase or created a brand new HD wallet, you can refer the private key of one of it's derived addresses with `hdw::a/b/c.`

For example, if you want to make an IOTX transfer from the first HD Wallet derived address, here is how you'd do it:

```
ioctl action transfer io1m22v9cnnjcktas584wcl96vl5z5e700l7fdvhk 10 -s hdw::1/1/1
```

or, an ioUSDT ERC20 transfer from the first derived address, would look like this:

```bash
ioctl xrc20 transfer io1m22v9cnnjcktas584wcl96vl5z5e700l7fdvhk 10 -c io1d77dcytfk5fsck089eg7669gfpqunrx35ue5ln -s hdw::1/1/1
```

where `io1m22v9cnnjcktas584wcl96vl5z5e700l7fdvhk` is the recipient and `io1d77dcytfk5fsck089eg7669gfpqunrx35ue5ln` is the ioUSDT token contract address on IoTeX.

### Export the HD Wallet <a href="#export-the-hd-wallet" id="export-the-hd-wallet"></a>

Displays the mnemonic phrase for the HD wallet

**#Example**

`Usage: ioctl hdwallet export`

**Example**

```
➜ ioctl hdwallet export
Enter password
# Type your password here
Mnemonic phrase: cattle success creek mean element useless lonely differ physical federal obtain knife
It is used to recover your wallet in case you forgot the password. Write them down and store it in a safe place.

```

### Import a mnemonic phrase <a href="#import-the-hd-wallet-from-the-mnemonic-phrase" id="import-the-hd-wallet-from-the-mnemonic-phrase"></a>

`Usage: ioctl hdwallet import`

```
➜ ioctl hdwallet import
Enter 12 mnemonic words you saved, separated by space

#cattle success creek mean element useless lonely differ physical federal obtain knife
Set password
# Type your password
Enter password again
# Re-type your password
Mnemonic phrase: cattle success creek mean element useless lonely differ physical federal obtain knife
It is used to recover your wallet in case you forgot the password. Write them down and store it in a safe place.
```

##
