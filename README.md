# ERC721-Royalty-NFT-EIP-2981-
ERC721 Royalty NFT (EIP‑2981)
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/common/ERC2981.sol";
import "@openzeppelin/contracts/token/ERC721/ERC721.sol";

contract RoyaltyNFT is ERC721, ERC2981 {
    uint256 public nextId;

    constructor() ERC721("RoyaltyNFT", "RNFT") {
        _setDefaultRoyalty(msg.sender, 500); // 5%
    }

    function mint() public {
        _mint(msg.sender, nextId++);
    }

    function supportsInterface(bytes4 interfaceId)
        public view override(ERC721, ERC2981)
        returns (bool)
    {
        return super.supportsInterface(interfaceId);
    }
}
