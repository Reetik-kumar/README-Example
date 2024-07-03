# Project Title

Solidity beginner assessment

## Description

This Solidity contract, named `MyToken`, is a simple implementation of a basic cryptocurrency token system on the Ethereum blockchain. The contract defines three public variables to store the token's name, abbreviation, and total supply. Additionally, it utilizes a mapping to track the balances of different addresses, effectively functioning as a ledger that records how many tokens each address holds. The contract includes two crucial functions: `mint` and `burn`. The `mint` function allows new tokens to be created and assigned to a specified address, thereby increasing both the total supply of tokens and the balance of that address. Conversely, the `burn` function permits the destruction of tokens from a specified address, decreasing both the total supply and the balance of that address. This function also includes a safeguard to ensure that the address has sufficient tokens to burn. This simple token contract can be used as a foundation for creating a digital currency or asset on the blockchain, facilitating various applications such as reward systems, digital collectibles, or even as a basis for more complex financial instruments. The contract ensures transparency and security in token creation and destruction, maintaining an accurate and immutable record of token balances and transactions on the Ethereum blockchain.

## Getting Started

### Executing program

// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

contract MyToken {

    string public tokenName = "MyToken";
    string public tokenAbbrv = "MTK";
    uint256 public totalSupply;
    
    mapping(address => uint256) public balances;

    function mint(address _address, uint256 _value) public {
        totalSupply += _value;
        balances[_address] += _value;
    }

    function burn(address _address, uint256 _value) public {
        require(balances[_address] >= _value, "Insufficient balance to burn");
        totalSupply -= _value;
        balances[_address] -= _value;
    }
}


