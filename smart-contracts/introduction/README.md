# Deploy an XRC20 Token

IoTeX fully supports `ERC20` and `ERC721` Ethereum token standards so that you can port any existing Ethereum token to IoTeX with no changes to the code. In IoTeX, `XRC20` is the name of the token standard equivalent to the Ethereum `ERC20` standard, while `XRC721` is the equivalent for the `ERC721`.

We will deploy a standard fungible token on the IoTeX blockchain in the following tutorials: first using the popular Remix IDE for Ethereum, then using native IoTeX tools. 

## The source code

The source code of the token will make use of the popular OpenZeppelin implementation, and is listed below:

```cpp
pragma solidity ^0.5.0;

import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/release-v2.5.0/contracts/GSN/Context.sol";
import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/release-v2.5.0/contracts/token/ERC20/ERC20.sol";
import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/release-v2.5.0/contracts/token/ERC20/ERC20Detailed.sol";

/**
 * @title SimpleToken
 * @dev Very simple ERC20 Token example, where all tokens are pre-assigned to the creator.
 * Note they can later distribute these tokens as they wish using `transfer` and other
 * `ERC20` functions.
 */
contract SimpleToken is Context, ERC20, ERC20Detailed {

    /**
     * @dev Constructor that gives _msgSender() all of existing tokens.
     */
    constructor () public ERC20Detailed("SimpleToken", "SIM", 18) {
        _mint(_msgSender(), 10000 * (10 ** uint256(decimals())));
    }
}

```



