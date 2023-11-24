# Types of Functions

This project is a solidity smart contract that inherits from the OpenZeppelin ERC-20 implementation and the Ownable contract provides ownership functionality. Only the contract owner can mint tokens, and any user can transfer or burn tokens.

## Description

This ERC-20 token, utilizing the Ownable contract, combines standard Ethereum compatibility with exclusive owner rights for minting and burning. It offers flexibility for token issuance, governance, and liquidity provision, with a smooth ownership transfer feature. Emphasizing cautious access controls and secure key management, the token serves as a flexible tool for regulated token ecosystems on Ethereum platforms.

## Getting Started

### Executing program

To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., HelloWorld.sol). Here is an example code of my error handling:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.18;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract MyToken is ERC20, Ownable {
    constructor(address initialOwner, uint256 initialSupply) ERC20("MyToken", "MYT") Ownable(initialOwner) {
        _mint(initialOwner, initialSupply);
    }

    function mint(address account, uint256 amount) external onlyOwner {
        _mint(account, amount);
    }

    function burn(uint256 amount) external {
        require(amount > 0, "Amount should be greater than 0");
        require(amount <= balanceOf(msg.sender), "Insufficient balance to burn");

        _burn(msg.sender, amount);
    }

    function transfer(address to, uint256 amount) public override returns (bool) {
        _transfer(_msgSender(), to, amount);
        return true;
    }
}
```
To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar and then click on the "Compile [file_name].sol" button. Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. 

To check if the code works as it should, you can deploy the contract by selecting the "Deploy & Run Transactions" tab from the left-hand sidebar once the code has been compiled. After choosing the "MyToken" contract from the drop-down menu, set an initial owner by copying an address above and an initial amount for that account. Then, press the "Deploy" button.

Once the contract is deployed, you should see the functions that you made. you can interact with it by trying to mint and burn tokens with the desired account.

Thank you!

## Authors

Aziel Samaniego

202011004@fit.edu.ph
