# Web3 Learning Journey

## About
This repository documents my journey learning Web3 development with Python.

## Environment
- Python 3.10+
- web3.py
- Ubuntu Linux

## Weekly Progress

### Week 1: Environment Setup & Git
- ✅ Installed Python 3.10+ and web3.py
- ✅ Set up Git and GitHub
- ✅ Created first repository
- ✅ Learned basic Git commands

## Resources
- [web3.py Documentation](https://web3py.readthedocs.io/)
- [Git Documentation](https://git-scm.com/doc)

## Goals
- Master Web3 development
- Build decentralized applications
- Contribute to blockchain ecosystem

----------------------------------------------------------------

## Week 2: RPC Basics

### What I Learned
- JSON-RPC protocol: How to communicate with Ethereum nodes using HTTP requests
- Block structure: Understanding block numbers, hashes, timestamps, and transactions
- Wei vs Ether: 1 ETH = 1,000,000,000,000,000,000 Wei (10^18)
- RPC rate limits: Free tier typically allows 100-300 requests per second

### Scripts Created

#### get_latest_block.py
Fetches and displays information about the latest block on Ethereum mainnet.

**Usage:**
```bash
python3 scripts/get_latest_block.py
```

#### get_eth_balance.py
Checks ETH balance for any Ethereum address.

**Usage:**
```bash
# With example addresses
python3 scripts/get_eth_balance.py

# With specific address
python3 scripts/get_eth_balance.py 0xYOUR_ADDRESS_HERE
```

### Key Concepts

**JSON-RPC**: A lightweight remote procedure call protocol using JSON for data encoding.

**Block Numbers vs Block Hashes**:
- Block number: Sequential integer (e.g., 18500000)
- Block hash: Unique 32-byte identifier (e.g., 0xabc123...)

**Wei Conversions**:
- 1 Wei = smallest unit
- 1 Gwei = 1,000,000,000 Wei (10^9)
- 1 Ether = 1,000,000,000,000,000,000 Wei (10^18)

**RPC Rate Limits**:
- Free tier: ~100-300 requests/second
- Implement rate limiting in production
- Cache frequently accessed data

----------------------------------------------------------------

----------------------------------------------------------------

## Week 3: Wallets & Private Keys

### What I Learned
- **Private Key Cryptography**: How ECDSA (Elliptic Curve Digital Signature Algorithm) creates key pairs
- **HD Wallets (BIP39/BIP44)**: One mnemonic phrase can generate infinite addresses deterministically
- **Derivation Paths**: Standard Ethereum path is m/44'/60'/0'/0/X (BIP44 standard)
- **Message Signing**: Prove wallet ownership without sending transactions (EIP-191)
- **Transaction Signing**: Understanding nonce management and gas estimation
- **Security Best Practices**: Never commit private keys, use .env files, validate inputs

### Scripts Created

#### generate_wallet.py
Generates new Ethereum wallets with private keys, public keys, and addresses.

**Usage:**
```bash
python3 scripts/generate_wallet.py
```

#### generate_hd_wallet.py
Creates HD wallets using BIP39 mnemonic phrases with multiple derived accounts.

**Usage:**
```bash
python3 scripts/generate_hd_wallet.py
```

#### explore_derivation_paths.py
Demonstrates how different BIP44 derivation paths create different addresses from the same seed.

**Usage:**
```bash
python3 scripts/explore_derivation_paths.py
```

#### sign_message.py
Sign and verify messages using Ethereum private keys (EIP-191 standard).

**Usage:**
```bash
python3 scripts/sign_message.py
```

#### sign_transaction.py
Sign transactions offline with proper nonce management (doesn't broadcast to network).

**Usage:**
```bash
python3 scripts/sign_transaction.py
```

#### estimate_gas.py
Estimate gas costs for transactions at different priority levels.

**Usage:**
```bash
python3 scripts/estimate_gas.py
```

#### wallet_manager.py (Week 3 Deliverable)
Comprehensive wallet management tool with all Week 3 features and security best practices.

**Features:**
- Generate random wallets
- Generate HD wallets with mnemonics
- Import from private key or mnemonic
- Sign and verify messages
- Check balances and nonces
- Secure input handling (hidden private keys)

**Usage:**
```bash
python3 scripts/wallet_manager.py
```

### Key Concepts

**Private Key → Public Key → Address Flow**:
```
Private Key (256 bits)
    ↓ (ECDSA)
Public Key (512 bits)
    ↓ (Keccak-256)
Address (160 bits / 20 bytes)
```

**BIP44 Derivation Path Structure**: m/44'/60'/0'/0/0
- 44' = Purpose (BIP44)
- 60' = Coin Type (Ethereum)
- 0' = Account index
- 0 = Chain (0=external, 1=change)
- 0 = Address index

**Message Signing vs Transaction Signing**:
- **Message signing**: Prove ownership without gas costs
- **Transaction signing**: Authorizes state changes on blockchain

**Nonce Management**:
- Sequential number for each transaction from an address
- Prevents replay attacks
- Must increment without gaps
- Current nonce = transaction count

**Gas Price Strategies**:
- Slow: ~80% of average (10+ minutes)
- Average: Current network rate (3-5 minutes)
- Fast: ~120% of average (1-2 minutes)
- Instant: ~150% of average (~30 seconds)

### Security Practices Implemented
✅ `.gitignore` prevents committing sensitive files
✅ `.env` for storing configuration (never committed)
✅ Hidden input for private keys using `getpass`
✅ Clear warnings about test-only usage
✅ Input validation for addresses and keys
✅ Secure random number generation for key creation

### Resources Used
- [BIP39 Specification](https://github.com/bitcoin/bips/blob/master/bip-0039.mediawiki)
- [BIP44 Specification](https://github.com/bitcoin/bips/blob/master/bip-0044.mediawiki)
- [EIP-191: Signed Data Standard](https://eips.ethereum.org/EIPS/eip-191)
- [eth-account Documentation](https://eth-account.readthedocs.io/)

----------------------------------------------------------------
