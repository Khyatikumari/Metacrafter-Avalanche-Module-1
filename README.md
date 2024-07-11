# Metacrafter-Avalanche-Module-1
// SPDX-License-Identifier: MIT
/*For this project, write a smart contract that implements the require(), assert() and revert() statements.*/
pragma solidity ^0.8.0;

contract AccountBalances{
    // mapping variable here
    mapping(address => uint) public account;

    function add(uint _val) public payable {
        require(_val > 0, "value of amount must be greater than zero");
        account[msg.sender] += _val;
    }

    // Function to withdraw funds
    function withdraw(uint _val) public {
        require(_val <= account[msg.sender], "withdraw amount is greater than balance amount");
        account[msg.sender] -= _val;
    }

    // Function to check the balance
    function checkBalance() public view returns (uint) {
        if(account[msg.sender] <= 0){
             revert("balance is less than or equal to zero");
        }
        assert(account[msg.sender] >= 0); 
        return account[msg.sender];
    }
}
