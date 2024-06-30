// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "https://github.com/OpenZeppelin/openzeppelin-solidity/contracts/token/ERC20/ERC20.sol";
import "https://github.com/OpenZeppelin/openzeppelin-solidity/contracts/access/Ownable.sol";
import "https://github.com/OpenZeppelin/openzeppelin-solidity/contracts/token/ERC20/extensions/ERC20Burnable.sol";

abstract contract DegenToken is ERC20, Ownable, ERC20Burnable {
    // Create a mapping to store the redemption values for each choice
    mapping(uint256 => uint256) private redemptionValues;

    constructor() ERC20("DegenToken", "DTK") {
        // Initialize the redemption values for each choice
        redemptionValues[1] = 100; // Legendary Sword NFT value = 100
        redemptionValues[2] = 50;  // Dragon Shield value = 50
        redemptionValues[3] = 25;  // Magic Potion value = 25
    }

    function mint(address to, uint256 amount) public onlyOwner {
        _mint(to, amount);
    }

    function burnTokens(uint256 amount) public {
        require(balanceOf(msg.sender) >= amount, "Insufficient balance");
        _burn(msg.sender, amount);
    }

    function checkBalance() public view returns (uint) {
        return balanceOf(msg.sender);
    }

    function transferTokensTo(address _receiver, uint256 amount) public {
        require(balanceOf(msg.sender) >= amount, "Insufficient balance");
        _transfer(msg.sender, _receiver, amount);
    }

    function gameStore() public pure returns (string[] memory) {
        string[] memory items = new string[](3);
        items[0] = "1. The titan value = 100";
        items[1] = "2. Heroshima value = 50";
        items[2] = "3. Magic Potion value = 25";
        return items;
    }

    function redeemTokens(uint256 choice) public payable {
        require(choice >= 1 && choice <= 3, "Invalid selection");

        uint256 amountToRedeem = redemptionValues[choice];
        require(amountToRedeem > 0, "Invalid choice");

        require(balanceOf(msg.sender) >= amountToRedeem, "Insufficient balance");

        // Transfer tokens from the sender to the contract owner
        _transfer(msg.sender, owner(), amountToRedeem);
    }
}
