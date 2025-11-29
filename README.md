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


