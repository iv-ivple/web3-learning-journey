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

----------------------------------------------------------------

## Week 4: ERC-20 Token Interaction

### What I Learned
- **ABIs (Application Binary Interface)**: The contract's "instruction manual" that defines functions, parameters, and return types
- **Function Selectors**: First 4 bytes of `keccak256(functionSignature)` used to identify contract functions
- **Contract Instances**: Python objects representing smart contracts with their address and ABI
- **Token Decimals**: ERC-20 balances are stored as integers; decimals define the conversion (e.g., USDC=6, DAI=18)
- **Read-Only Functions**: `view`/`constant` functions don't modify state and don't cost gas
- **Return Value Decoding**: How web3.py automatically decodes contract responses based on ABI
- **ERC-20 Standard**: All compliant tokens share the same interface (name, symbol, decimals, balanceOf, totalSupply)

### Scripts Created

#### explore_abi.py
Explains ABI structure and demonstrates function selectors.

**Usage:**
```bash
python3 scripts/week4/explore_abi.py
```

#### connect_to_token.py
Connects to popular ERC-20 tokens and fetches basic metadata.

**Usage:**
```bash
python3 scripts/week4/connect_to_token.py
```

#### check_balance.py
Checks ERC-20 token balances for Ethereum addresses.

**Usage:**
```bash
python3 scripts/week4/check_balance.py [ADDRESS]
```

#### token_metadata.py
Fetches comprehensive metadata for popular ERC-20 tokens.

**Usage:**
```bash
python3 scripts/week4/token_metadata.py
```

#### erc20_balance_checker.py (Week 4 Deliverable)
Comprehensive ERC-20 balance checker that works with any token address.

**Features:**
- Works with any ERC-20 token (by address or popular token name)
- Fetches complete token metadata (name, symbol, decimals, total supply)
- Checks balances for one or multiple addresses
- User-friendly output with proper formatting
- Error handling and address validation
- Supports token name shortcuts (USDC, DAI, WETH, UNI, LINK)

**Usage:**
```bash
# With examples
python3 scripts/erc20_balance_checker.py --examples

# Check USDC balance
python3 scripts/erc20_balance_checker.py USDC 0xYOUR_ADDRESS

# Check multiple balances
python3 scripts/erc20_balance_checker.py DAI 0xADDRESS1 0xADDRESS2

# Use full token address
python3 scripts/erc20_balance_checker.py 0xTOKEN_ADDRESS 0xWALLET_ADDRESS
```

### Key Concepts

**ABI Structure**:
```json
{
  "name": "balanceOf",
  "type": "function",
  "inputs": [{"name": "_owner", "type": "address"}],
  "outputs": [{"name": "balance", "type": "uint256"}],
  "constant": true
}
```

**Function Selector Calculation**:
- `balanceOf(address)` → `keccak256("balanceOf(address)")[:4]` → `0x70a08231`
- Used to identify which function to call in the contract
- First 4 bytes of the function signature hash

**Creating Contract Instances**:
```python
contract = w3.eth.contract(address=TOKEN_ADDRESS, abi=ERC20_ABI)
balance = contract.functions.balanceOf(address).call()
```

**Token Decimal Conversion**:
```python
raw_balance = 1000000  # From contract
decimals = 6  # USDC has 6 decimals
actual_balance = raw_balance / (10 ** decimals)  # 1.0 USDC
```

**ERC-20 Standard Functions**:
- `name()` → Returns token name (e.g., "USD Coin")
- `symbol()` → Returns token symbol (e.g., "USDC")
- `decimals()` → Returns decimal places (e.g., 6)
- `totalSupply()` → Returns total token supply
- `balanceOf(address)` → Returns balance for an address

**Popular ERC-20 Tokens**:
- **USDC** (USD Coin): 6 decimals, stablecoin backed by Circle
- **DAI**: 18 decimals, decentralized stablecoin by MakerDAO
- **WETH** (Wrapped Ether): 18 decimals, ERC-20 wrapper for ETH
- **UNI** (Uniswap): 18 decimals, DEX governance token
- **LINK** (Chainlink): 18 decimals, oracle network token

**Read vs Write Operations**:
- **Read (call)**: Free, returns data, doesn't change state
  - Example: `balanceOf()`, `totalSupply()`
- **Write (transaction)**: Costs gas, changes state, requires signing
  - Example: `transfer()`, `approve()` (covered in Week 5)

### Resources Used
- [ERC-20 Token Standard](https://eips.ethereum.org/EIPS/eip-20)
- [web3.py Contract Documentation](https://web3py.readthedocs.io/en/stable/contracts.html)
- [Ethereum ABI Specification](https://docs.soliditylang.org/en/latest/abi-spec.html)
- [Etherscan Token Tracker](https://etherscan.io/tokens)

----------------------------------------------------------------

## Week 5: Transaction History & Events

### What I Learned
- **Event Logs**: How Ethereum logs work and their structure
- **Topics vs Data**: Indexed parameters in topics, non-indexed in data
- **Transfer Event**: Standard ERC-20 Transfer(address,address,uint256) event
- **Event Filtering**: Using eth_getLogs with topic filters
- **Pagination**: Handling RPC limits by fetching in chunks
- **Block Ranges**: Managing large historical queries
- **Transaction Receipts**: Extracting gas costs and event logs

### Scripts Created

#### explore_events.py - understanding event logs & topics
#### fetch_transaction_history.py - fetch events
#### parse_receipts.py - understanding transaction receipts
#### filter_transfer_events.py - filter logs event signature
#### paginated_event_fetcher.py - RCP block range limits, pagination, rate limiting
#### token_transfer_history.py - fetch all transfer events and generate CSV with number of information

### Key Concepts

**Transfer Event Structure**:
```
Event: Transfer(address indexed from, address indexed to, uint256 value)
Signature: 0xddf252ad...
Topic[0]: Event signature
Topic[1]: from address (indexed)
Topic[2]: to address (indexed)
Data: amount (non-indexed)
```

[Continue with other key concepts...]
```

---

## **Key Concepts Summary**

### Event Logs
Events are stored in the blockchain's transaction receipts as logs. Each log contains:
- **address**: The contract that emitted the event
- **topics**: Array of indexed parameters (max 4, first is event signature)
- **data**: Non-indexed parameters (ABI encoded)

### Topics Explained
```
topics[0] = keccak256("Transfer(address,address,uint256)")
topics[1] = from address (32 bytes, padded)
topics[2] = to address (32 bytes, padded)
data = amount (32 bytes, uint256)


