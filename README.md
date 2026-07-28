# B20Token.sol
B20Token.sol
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract HOPE is ERC20, Ownable {
    uint8 private _decimals;

    constructor() 
        ERC20("HOPE", "HOPE") 
        Ownable(msg.sender) 
    {
        _decimals = 18;
        _mint(msg.sender, 1000000000 * 10 ** 18);
    }

    function decimals() public view virtual override returns (uint8) {
        return _decimals;
    }

    function mint(address to, uint256 amount) public onlyOwner {
        _mint(to, amount);
    }

    function burn(uint256 amount) public {
        _burn(msg.sender, amount);
    }
}
