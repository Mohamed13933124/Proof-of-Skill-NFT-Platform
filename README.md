# 🎓 Proof-of-Skill NFT Platform

A decentralized application (DApp) built on the **Celo blockchain** that allows users to claim and verify their professional skills as NFT certificates. This platform provides an immutable, on-chain proof of skills that can be shared across the Web3 ecosystem.

## 🌟 Overview

The Proof-of-Skill NFT Platform transforms traditional skill verification into a blockchain-powered certification system. Users can claim skill certificates in various domains (Coding, Design, Marketing) which are minted as ERC-721 NFTs on the Celo network. These certificates serve as verifiable, portable credentials that demonstrate expertise.

## ✨ Features

### 🔐 Blockchain-Powered Verification
- **Immutable Certificates**: All skill certificates are stored permanently on the Celo blockchain
- **Decentralized Ownership**: Users have complete control over their certificates as NFTs
- **Transparent Verification**: Anyone can verify certificate authenticity on-chain

### 💼 Multi-Skill Certification
- **Coding**: Certifies proficiency in programming and software development
- **Design**: Validates expertise in UI/UX and visual design principles
- **Marketing**: Confirms knowledge in digital marketing and growth strategies

### 🎨 Professional Interface
- **Modern Design**: Built with Tailwind CSS featuring a professional blue/gold/white theme
- **Responsive Layout**: Fully functional on desktop and mobile devices
- **Intuitive Navigation**: Easy-to-use interface with clear sections

### 🦊 MetaMask Integration
- **One-Click Connection**: Seamless wallet integration with MetaMask
- **Automatic Network Switching**: Auto-detects and switches to Celo Mainnet
- **Real-Time Updates**: Live balance and certificate tracking

## 🏗️ Architecture

### Smart Contract (`SkillCert.sol`)

The smart contract is a simplified ERC-721 implementation with the following key features:

- **Minting Function**: `mintCertificate(string memory skillName)` - Creates a new NFT certificate
- **Query Function**: `getUserCertificates(address user)` - Returns all skills owned by a user
- **Ownership Tracking**: Standard ERC-721 `ownerOf` and `balanceOf` functions
- **Skill Metadata**: Each token stores the associated skill name on-chain

### Frontend (`index.html`)

Single-page application with three main sections:

1. **Home**: Landing page explaining the platform's value proposition
2. **Available Skills**: Browse and claim skill certificates
3. **My Certificates**: View all owned NFT certificates

## 🚀 Getting Started

### Prerequisites

- **MetaMask Wallet**: Install from [metamask.io](https://metamask.io)
- **Celo Network**: The DApp will automatically configure this for you
- **CELO Tokens**: Required for transaction gas fees

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd "Proof-of-Skill NFT Platform"
   ```

2. **Deploy the Smart Contract**

   - Open [Remix IDE](https://remix.ethereum.org)
   - Create a new file named `SkillCert.sol`
   - Copy the contract code from `SkillCert.sol`
   - Compile with Solidity ^0.8.0
   - Deploy to Celo Mainnet:
     - Set Remix environment to "Injected Provider - MetaMask"
     - Ensure MetaMask is connected to Celo Mainnet
     - Click "Deploy"
     - Confirm the transaction in MetaMask

3. **Configure the Frontend**

   Open `index.html` and update the contract address:
   ```javascript
   const CONTRACT_ADDRESS = "0xYourDeployedContractAddress";
   ```
   Replace with your actual deployed contract address.

4. **Launch the DApp**

   Simply open `index.html` in a web browser. No server required!

## 📖 Usage Guide

### Connecting Your Wallet

1. Click the **"Connect Wallet"** button in the navigation bar
2. MetaMask will prompt you to connect
3. Approve the connection request
4. The DApp will automatically switch to Celo Mainnet (Chain ID: 42220)
5. If Celo is not in your MetaMask, it will be added automatically

### Claiming a Certificate

1. Navigate to **"Available Skills"** section
2. Choose a skill certificate (Coding, Design, or Marketing)
3. Click **"Claim Certificate"** on the desired skill
4. Confirm the transaction in MetaMask
5. Wait for blockchain confirmation
6. Success! Your certificate is minted

### Viewing Your Certificates

1. Navigate to **"My Certificates"** section
2. All your owned NFT certificates will be displayed
3. Each card shows:
   - Skill name and icon
   - Certificate number
   - Owner address
   - Verification status

## 🌐 Celo Network Details

- **Network Name**: Celo Mainnet
- **Chain ID**: 42220 (0xa4ec in hex)
- **RPC URL**: https://forno.celo.org
- **Block Explorer**: https://explorer.celo.org
- **Native Currency**: CELO

### Why Celo?

- **Fast & Affordable**: Low transaction fees and quick confirmation times
- **Mobile-First**: Optimized for mobile-first Web3 experiences
- **Carbon Negative**: Environmentally sustainable blockchain
- **EVM Compatible**: Works with Ethereum tools and standards

## 💻 Technical Stack

- **Frontend**: HTML5, Tailwind CSS, JavaScript
- **Web3 Library**: Ethers.js v5.2
- **Smart Contract**: Solidity ^0.8.0
- **Blockchain**: Celo Mainnet
- **Wallet**: MetaMask

## 📜 Smart Contract Functions

### Public Functions

```solidity
// Mint a new skill certificate
function mintCertificate(string memory skillName) public returns (uint256)

// Get all certificates owned by a user
function getUserCertificates(address user) public view returns (string[] memory)

// Get the owner of a specific token
function ownerOf(uint256 tokenId) public view returns (address)

// Get the number of tokens owned by an address
function balanceOf(address owner) public view returns (uint256)

// Get the skill name for a token
function getSkillName(uint256 tokenId) public view returns (string memory)

// Get all token IDs owned by a user
function getUserTokenIds(address user) public view returns (uint256[] memory)

// Get the total number of minted tokens
function totalSupply() public view returns (uint256)
```

## 🔒 Security Considerations

- **No External Dependencies**: The smart contract doesn't import external libraries, reducing attack surface
- **Zero Address Checks**: Prevents minting to or querying the zero address
- **Duplicate Prevention**: Ensures tokens can't be double-minted
- **Immutable Certificates**: Once minted, certificates cannot be modified or deleted

## 🎯 Use Cases

### For Individuals
- **Portable Credentials**: Carry your skill proofs across platforms
- **Professional Branding**: Showcase verifiable expertise to employers
- **Web3 Resume**: Build an on-chain professional profile

### For Organizations
- **Verified Hiring**: Check candidate skills directly on-chain
- **Training Completion**: Issue certificates for course completion
- **Team Building**: Verify team member competencies

### For Educational Institutions
- **Digital Diplomas**: Issue blockchain-based credentials
- **Lifelong Learning**: Track continuous skill development
- **Alumni Network**: Create verifiable alumni credentials

## 🛠️ Customization

### Adding New Skills

1. **Update Frontend**: Add a new skill card in the "Available Skills" section
2. **Update Icons**: Choose appropriate emoji or icon
3. **Update Colors**: Assign a unique color scheme
4. **No Contract Changes Needed**: The contract accepts any skill name

### Styling Modifications

The application uses Tailwind CSS. Key design elements:

- **Primary Colors**: Blue (#1e40af, #3b82f6)
- **Accent Color**: Gold (#FFD700)
- **Background**: Purple gradient
- **Fonts**: System fonts with bold headings

## 📝 Development Roadmap

- [ ] Implement skill verification mechanism (e.g., quiz/test)
- [ ] Add skill expiration dates
- [ ] Enable certificate revocation for organizations
- [ ] Integrate with decentralized identity (DID) systems
- [ ] Add IPFS metadata storage for detailed certificates
- [ ] Implement certificate sharing on social media
- [ ] Create marketplace for skill-based opportunities

## 🤝 Contributing

Contributions are welcome! Please feel free to submit pull requests or open issues for bugs and feature requests.

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgments

- **Celo Foundation** for the sustainable blockchain infrastructure
- **MetaMask** for the Web3 wallet integration
- **OpenZeppelin** for smart contract standards inspiration
- **Tailwind CSS** for the utility-first CSS framework

## 📞 Support

For questions or support:
- Create an issue in the GitHub repository
- Check the Celo documentation: [docs.celo.org](https://docs.celo.org)
- Join the Celo Discord community

---

**Built with ❤️ for the Web3 community on Celo**

*Empowering professionals with blockchain-verified skills*
