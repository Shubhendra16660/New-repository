This Solidity contract, MyToken, defines a simple ERC-20-like token with basic functionalities such as minting and burning tokens. The contract is built on Solidity version 0.8.18. Below, you'll find an overview of the key components and functionalities implemented in the contract.

Requirements
Public Variables:

Token Name: The name of the token is Shubh.
Token Abbreviation: The abbreviation for the token is SHA.
Total Supply: The total supply of the token, which is initialized to 0.
Mapping:

The contract includes a mapping from addresses to balances (address => uint). This keeps track of the token balance for each address.
Mint Function:

The mint function takes two parameters: an address and a value.
It increases the total supply by the specified value.
It increases the balance of the specified address by the same amount.
Burn Function:

The burn function takes two parameters: an address and a value.
It decreases the total supply by the specified value.
It decreases the balance of the specified address by the same amount.
It includes a conditional check to ensure that the balance of the specified address is greater than or equal to the amount to be burned.
Contract Code
solidity
Copy code
// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

contract MyToken {

    // Public variables
    string public tokenName = "Shubh";
    string public tokenAbbrv = "SHA";
    uint public totalSupply = 0;

    // Mapping to store balances
    mapping(address => uint) public balances;

    // Mint function to create new tokens
    function mint(address _address, uint _value) public {
        totalSupply += _value;
        balances[_address] += _value;
    }

    // Burn function to destroy tokens
    function burn(address _address, uint _value) public {
        if (balances[_address] >= _value) {
            totalSupply -= _value;
            balances[_address] -= _value;
        }
    }
}
Usage
Minting Tokens
To mint tokens, call the mint function with the desired address and amount of tokens to be created. This increases the total supply of tokens and the balance of the specified address.

solidity
Copy code
mint(address _address, uint _value)
_address: The address to which the minted tokens will be added.
_value: The amount of tokens to be minted.
Burning Tokens
To burn tokens, call the burn function with the desired address and amount of tokens to be destroyed. This decreases the total supply of tokens and the balance of the specified address, provided that the address has a sufficient balance.

solidity
Copy code
burn(address _address, uint _value)
_address: The address from which the tokens will be burned.
_value: The amount of tokens to be burned.
Example
Here is an example of how to use the contract:

solidity
Copy code
// Deploy the contract
MyToken myToken = new MyToken();

// Mint 100 tokens to address 0x123...
myToken.mint(0x123..., 100);

// Burn 50 tokens from address 0x123...
myToken.burn(0x123..., 50);
Conclusion
This MyToken contract provides basic functionalities for a simple token system, including the ability to mint and burn tokens. It serves as a foundational example for understanding how token contracts work in Solidity. Further enhancements and features can be added to extend the functionality of this token contract.
