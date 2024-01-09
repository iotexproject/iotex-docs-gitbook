# XRC20 Tokens

### Transfer Tokens <a href="#transfer-token-on-erc20-contract" id="transfer-token-on-erc20-contract"></a>

`Usage: ioctl xrc20 transfer ALIAS|TARGET_ADDRESS AMOUNT -c ALIAS|CONTRACT_ADDRESS [-l GAS_LIMIT] -s SIGNER [-p GAS_PRICE]`

```
➜   ioctl xrc20 transfer io1juvx5g063eu4ts832nukp4vgcwk2gnc5cu9ayd 4 -c io1y9ndaezjrdlkw93hquqru7txh9jcsmtmrvt4yw -s ALIAS -l 50000
Enter password #ioxxx...xxx:
...
...
Action has been sent to blockchain.
Wait for several seconds and query this action by hash:iotexscan.io/action/xxx...xxx
```

### Transfer Token From Another Address On Erc20 Contract <a href="#transfer-token-from-another-address-on-erc20-contract" id="transfer-token-from-another-address-on-erc20-contract"></a>

`Usage: ioctl xrc20 transferFrom ALIAS|OWNER_ADDRESS ALIAS|TARGET_ADDRESS AMOUNT -c ALIAS|CONTRACT_ADDRESS [-l GAS_LIMIT] -s SIGNER [-p GAS_PRICE]`

```
➜   ioctl xrc20 transferFrom io1q4enhh0tp5pqpa6s4urhwrx32529pmyyzdgu3q io1juvx5g063eu4ts832nukp4vgcwk2gnc5cu9ayd 4 -c io1y9ndaezjrdlkw93hquqru7txh9jcsmtmrvt4yw -s ALIAS -l 50000
Enter password #ioxxx...xxx:
...
...
Action has been sent to blockchain.
Wait for several seconds and query this action by hash:iotexscan.io/action/xxx...xxx
```

### Allow a Spender <a href="#allow-spender-withdraw-from-account-with-limitation" id="allow-spender-withdraw-from-account-with-limitation"></a>

`Usage: ioctl approve ALIAS|SPENDER_ADDRESS XRC20_AMOUNT -c ALIAS|CONTRACT_ADDRESS -s SIGNER [-l GAS_LIMIT]`

```
➜   ioctl xrc20 approve io1juvx5g063eu4ts832nukp4vgcwk2gnc5cu9ayd 4 -c io1y9ndaezjrdlkw93hquqru7txh9jcsmtmrvt4yw -s ALIAS -l 50000
Enter password #ioxxx...xxx:
...
...
Action has been sent to blockchain.
Wait for several seconds and query this action by hash:iotexscan.io/action/xxx...xxx

```

### Query Remaining Withdraw Amount For Spender <a href="#query-remaining-withdraw-amount-for-spender" id="query-remaining-withdraw-amount-for-spender"></a>

`Usage: ioctl allowance ALIAS|OWNER_ADDRESS ALIAS|SPENDER_ADDRESS -c ALIAS|CONTRACT_ADDRESS`

```
➜   ioctl xrc20 allowance io1q4enhh0tp5pqpa6s4urhwrx32529pmyyzdgu3q io1juvx5g063eu4ts832nukp4vgcwk2gnc5cu9ayd -c io1y9ndaezjrdlkw93hquqru7txh9jcsmtmrvt4yw
Raw output: 0000000000000000000000000000000000000000000000000000000000000004
Output in decimal: 4
```

### Query Total Token Supply On Erc20 Contract <a href="#query-total-token-supply-on-erc20-contract" id="query-total-token-supply-on-erc20-contract"></a>

`Usage: ioctl xrc20 totalSupply -c ALIAS|CONTRACT_ADDRESS`

```
➜   ioctl xrc20 totalSupply -c io1y9ndaezjrdlkw93hquqru7txh9jcsmtmrvt4yw
Raw output: 0000000000000000000000000000000000000000010f73e141e95768f6bfacac
Output in decimal: 328166124527934490560933036
```

### Query Account Balance On Erc20 Contract

`Usage: ioctl xrc20 balanceOf ALIAS|ACCOUNT_ADDRESS -c ALIAS|CONTRACT_ADDRESS`

```
➜   ioctl xrc20 balanceOf io1q4enhh0tp5pqpa6s4urhwrx32529pmyyzdgu3q -c io1y9ndaezjrdlkw93hquqru7txh9jcsmtmrvt4yw
Raw output: 000000000000000000000000000000000000000000000000b469471f80170d33
Output in decimal: 13000000000000199987
```
