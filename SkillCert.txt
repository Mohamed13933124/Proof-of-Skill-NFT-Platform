// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

/**
 * @title SkillCert
 * @dev ERC-721 Simplified Implementation for Skill Certificates on Celo
 * @notice This contract allows users to mint skill certificates as NFTs
 */
contract SkillCert {
    
    // Token name
    string public name = "SkillCertificate";
    
    // Token symbol
    string public symbol = "SKILLCERT";
    
    // Token ID counter
    uint256 private _tokenIdCounter;
    
    // Mapping from token ID to owner address
    mapping(uint256 => address) private _owners;
    
    // Mapping from owner to token count
    mapping(address => uint256) private _balances;
    
    // Mapping from token ID to skill name
    mapping(uint256 => string) private _tokenSkills;
    
    // Mapping from user address to list of their token IDs
    mapping(address => uint256[]) private _userTokens;
    
    // Mapping from token ID to index in owner's token list
    mapping(uint256 => uint256) private _tokenIndex;
    
    // Events
    event Transfer(address indexed from, address indexed to, uint256 indexed tokenId);
    event CertificateMinted(address indexed recipient, uint256 indexed tokenId, string skillName);
    
    /**
     * @dev Mints a new skill certificate NFT
     * @param skillName The name of the skill being certified
     * @return The ID of the newly minted token
     */
    function mintCertificate(string memory skillName) public returns (uint256) {
        require(bytes(skillName).length > 0, "Skill name cannot be empty");
        
        _tokenIdCounter++;
        uint256 newTokenId = _tokenIdCounter;
        
        _mint(msg.sender, newTokenId, skillName);
        
        emit CertificateMinted(msg.sender, newTokenId, skillName);
        
        return newTokenId;
    }
    
    /**
     * @dev Internal function to mint a token
     * @param to The address that will own the token
     * @param tokenId The token ID to mint
     * @param skillName The skill name associated with this certificate
     */
    function _mint(address to, uint256 tokenId, string memory skillName) internal {
        require(to != address(0), "Cannot mint to zero address");
        require(_owners[tokenId] == address(0), "Token already minted");
        
        _balances[to]++;
        _owners[tokenId] = to;
        _tokenSkills[tokenId] = skillName;
        
        // Add token to user's token list
        _tokenIndex[tokenId] = _userTokens[to].length;
        _userTokens[to].push(tokenId);
        
        emit Transfer(address(0), to, tokenId);
    }
    
    /**
     * @dev Returns the owner of a specific token
     * @param tokenId The ID of the token
     * @return The address of the token owner
     */
    function ownerOf(uint256 tokenId) public view returns (address) {
        address owner = _owners[tokenId];
        require(owner != address(0), "Token does not exist");
        return owner;
    }
    
    /**
     * @dev Returns the number of tokens owned by an address
     * @param owner The address to query
     * @return The number of tokens owned
     */
    function balanceOf(address owner) public view returns (uint256) {
        require(owner != address(0), "Cannot query zero address");
        return _balances[owner];
    }
    
    /**
     * @dev Returns the skill name associated with a token
     * @param tokenId The ID of the token
     * @return The skill name
     */
    function getSkillName(uint256 tokenId) public view returns (string memory) {
        require(_owners[tokenId] != address(0), "Token does not exist");
        return _tokenSkills[tokenId];
    }
    
    /**
     * @dev Returns all certificates (skill names) owned by a user
     * @param user The address of the user
     * @return An array of skill names
     */
    function getUserCertificates(address user) public view returns (string[] memory) {
        require(user != address(0), "Cannot query zero address");
        
        uint256[] memory tokenIds = _userTokens[user];
        string[] memory skills = new string[](tokenIds.length);
        
        for (uint256 i = 0; i < tokenIds.length; i++) {
            skills[i] = _tokenSkills[tokenIds[i]];
        }
        
        return skills;
    }
    
    /**
     * @dev Returns all token IDs owned by a user
     * @param user The address of the user
     * @return An array of token IDs
     */
    function getUserTokenIds(address user) public view returns (uint256[] memory) {
        require(user != address(0), "Cannot query zero address");
        return _userTokens[user];
    }
    
    /**
     * @dev Returns the total number of tokens minted
     * @return The total supply
     */
    function totalSupply() public view returns (uint256) {
        return _tokenIdCounter;
    }
    
    /**
     * @dev Checks if a token exists
     * @param tokenId The ID of the token to check
     * @return Boolean indicating if the token exists
     */
    function exists(uint256 tokenId) public view returns (bool) {
        return _owners[tokenId] != address(0);
    }
}
