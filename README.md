DegenToken Contract
The DegenToken contract is an Ethereum smart contract written in Solidity that implements a basic ERC20 token with additional functionalities for minting, burning, ownership management, and token redemption.

Features
ERC20 Standard: The contract inherits from ERC20.sol from OpenZeppelin, providing standard token functionalities such as transfer, balance inquiry, and allowance management.

Ownership: Utilizes Ownable.sol to restrict certain functions (like minting tokens) to be callable only by the contract owner.

Burnable Tokens: Extends ERC20 with burning capabilities using ERC20Burnable.sol, allowing token holders to burn their own tokens, effectively reducing the total supply.

Token Minting: Provides a mint function allowing the contract owner to mint new tokens and assign them to any address.

Token Redemption: Implements a redeemTokens function that allows token holders to redeem tokens for specific predefined items. Each item has a predetermined token value that is deducted from the token holder's balance and transferred to the contract owner.

Game Store Simulation: Includes a gameStore function that returns a list of strings describing the items available for redemption in a game store.

Setup and Usage
Deployment
Deploy the DegenToken contract on an Ethereum network (e.g., mainnet, testnet) using tools like Remix, Truffle, or Hardhat.
Interacting with the Contract
Minting Tokens: Call the mint function with the desired recipient address and token amount. This function is restricted to the contract owner.

Burning Tokens: Any token holder can call the burnTokens function to burn a specified amount of their own tokens.

Redeeming Tokens: Call the redeemTokens function with a choice (1, 2, or 3) corresponding to an item in the game store. This function deducts tokens from the caller's balance and transfers them to the contract owner.

Checking Balance: Use the checkBalance function to retrieve the token balance of the caller.

Transferring Tokens: Transfer tokens to another address using the transferTokensTo function, ensuring the caller has sufficient balance.

![image](https://github.com/manvichhabra12/ETH-AVAX-4/assets/171688694/80e940ab-9650-4fa7-95dd-f3de8a4bad3c)

License
This project is licensed under the MIT License - see the LICENSE file for details.

