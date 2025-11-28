# Web3 Learning Journey

## About
This repository documents my journey learning Web3 development with Python.

## Environment
- Python 3.10+
- web3.py
- Ubuntu Linux

## Weekly Progress

📘 Web3 Keeper Curriculum - Revised Edition
1-2 Hours/Day | Beginner → MakerDAO Keeper | 12-16 Months

🎯 Prerequisites You Already Have
    • ✅ Ubuntu/Linux CLI experience 
    • ✅ Python fundamentals 
    • ✅ Flask web API development 
    • ✅ Deployment experience (Render) 
🛠️ New Skills You'll Build
    • Git/GitHub workflow 
    • Blockchain fundamentals & RPC interaction 
    • Smart contract interaction via Python 
    • Testing & containerization 
    • MEV & keeper bot architecture 
    • Production-ready automation 

🌱 PHASE 1: Foundations (Weeks 1-10)
Goal: Understand blockchain mechanics and control it via Python
Week 1: Environment Setup & Git
Daily Tasks (1-2 hours):
    • Install Python 3.10+ and web3.py 
    • Set up Git and create GitHub account 
    • Create first repository: web3-learning-journey 
    • Learn basic Git commands (add, commit, push, branch) 
Deliverable: Repository with README documenting your learning path

Week 2: RPC Basics
Daily Tasks:
    • Sign up for Alchemy or Infura (free tier) 
    • Connect to Ethereum mainnet via RPC 
    • Write get_latest_block.py 
    • Write get_eth_balance.py 
Key Concepts:
    • JSON-RPC protocol 
    • Block numbers vs block hashes 
    • Wei vs Ether conversions 
    • Rate limits on free RPC tiers 
Deliverable: Two working scripts committed to GitHub

Week 3: Wallets & Private Keys
Daily Tasks:
    • Understand private key cryptography 
    • Generate wallets programmatically 
    • Sign messages with web3.py 
    • NEVER commit private keys (add .env and .gitignore) 
Key Concepts:
    • HD wallets and derivation paths 
    • Signing vs sending transactions 
    • Nonce management 
    • Gas price estimation 
Deliverable: Wallet generator script with proper security practices

Week 4: ERC-20 Token Interaction
Daily Tasks:
    • Understand ABIs (Application Binary Interface) 
    • Load ERC-20 contract 
    • Read token balances 
    • Fetch token metadata (name, symbol, decimals) 
Key Concepts:
    • Contract instances in web3.py 
    • Function selectors 
    • Return value decoding 
    • Popular ERC-20 tokens (USDC, DAI, WETH) 
Deliverable: erc20_balance_checker.py that works with any token address

Week 5: Transaction History & Events
Daily Tasks:
    • Fetch transaction history for an address 
    • Parse transaction receipts 
    • Filter ERC-20 Transfer events 
    • Handle pagination for large histories 
Key Concepts:
    • Event logs and topics 
    • Indexed vs non-indexed parameters 
    • Block ranges and API limits 
Deliverable: Script that generates CSV of all token transfers for a wallet

Week 6: Database Fundamentals
Daily Tasks:
    • Install PostgreSQL or use SQLite 
    • Learn basic SQL (CREATE, INSERT, SELECT, UPDATE) 
    • Design schema for wallet tracking 
    • Write Python database connector 
Key Concepts:
    • Normalization 
    • Indexes for performance 
    • SQL injection prevention 
    • SQLAlchemy ORM basics 
Deliverable: Database setup script and connection module

Week 7: Testing Basics
Daily Tasks:
    • Install pytest 
    • Write unit tests for previous scripts 
    • Learn mocking for RPC calls 
    • Achieve 70%+ code coverage 
Key Concepts:
    • Test-driven development 
    • Fixtures and parametrization 
    • Mocking external dependencies 
    • CI/CD basics 
Deliverable: Test suite for all Phase 1 scripts

Week 8-10: Flask Wallet Watcher API
Daily Tasks:
    • Design REST API endpoints 
    • Implement wallet registration 
    • Build background worker for monitoring 
    • Add basic authentication 
    • Deploy to Render 
Endpoints:
    • POST /wallets - Register wallet 
    • GET /wallets/{address} - Get wallet info 
    • GET /wallets/{address}/transactions - List transactions 
    • POST /wallets/{address}/alerts - Set balance alert 
Key Concepts:
    • RESTful design principles 
    • Background tasks (celery or APScheduler) 
    • Rate limiting 
    • Error handling and logging 
Deliverable: Working API deployed with documentation

⚙️ PHASE 2: Automation & Data (Weeks 11-24)
Goal: Build automated services that monitor and respond to blockchain events
Week 11-12: Docker & Deployment
Daily Tasks:
    • Learn Docker fundamentals 
    • Write Dockerfile for Wallet Watcher API 
    • Create docker-compose.yml with database 
    • Deploy containerized app 
Key Concepts:
    • Container vs VM 
    • Volumes and networking 
    • Environment variables in containers 
    • Multi-stage builds 
Deliverable: Dockerized version of Wallet Watcher API

Week 13-15: Telegram Bot Basics
Daily Tasks:
    • Create Telegram bot with BotFather 
    • Install python-telegram-bot 
    • Build command handlers 
    • Implement conversation flows 
Bot Commands:
    • /start - Welcome message 
    • /balance <address> - Check ETH balance 
    • /track <address> - Monitor wallet 
    • /gas - Current gas prices 
    • /price <token> - Token price from DEX 
Key Concepts:
    • Webhooks vs polling 
    • Message handlers and filters 
    • Inline keyboards 
    • Error handling for user input 
Deliverable: Working Telegram bot with 5+ commands

Week 16-18: Blockchain Indexing
Daily Tasks:
    • Learn about The Graph protocol 
    • Explore existing subgraphs 
    • Query GraphQL endpoints 
    • Compare indexed data vs direct RPC calls 
Key Concepts:
    • Why indexing matters 
    • GraphQL query syntax 
    • Pagination in The Graph 
    • Combining indexed data with real-time RPC 
Deliverable: Analytics script using The Graph for historical data

Week 19-21: Enhanced Analytics API
Daily Tasks:
    • Extend Wallet Watcher with analytics 
    • Add token portfolio tracking 
    • Implement caching layer (Redis) 
    • Build data aggregation endpoints 
New Endpoints:
    • GET /analytics/portfolio/{address} - Full portfolio breakdown 
    • GET /analytics/gas-spent/{address} - Historical gas analysis 
    • GET /analytics/token-flows/{address} - Inflow/outflow analysis 
Key Concepts:
    • Redis for caching 
    • Cache invalidation strategies 
    • Data aggregation patterns 
    • Performance optimization 
Deliverable: Production-grade analytics API

Week 22-24: DEX Price Monitor
Daily Tasks:
    • Understand Uniswap V2 formula (x * y = k) 
    • Calculate prices from pool reserves 
    • Monitor multiple DEXes (Uniswap, SushiSwap) 
    • Build price comparison dashboard 
Key Concepts:
    • Automated Market Makers (AMMs) 
    • Liquidity pools 
    • Slippage calculation 
    • Price impact 
Deliverable: Multi-DEX price monitoring service with Flask UI

🧠 PHASE 3: Keeper Mindset (Weeks 25-40)
Goal: Detect and react to profitable blockchain conditions
Week 25-27: MEV Fundamentals
Daily Tasks:
    • Read MEV research papers 
    • Study Flashbots documentation 
    • Understand mempool dynamics 
    • Analyze MEV transactions on Etherscan 
Key Concepts:
    • Front-running, back-running, sandwiching 
    • Priority gas auctions 
    • Bundle submissions 
    • MEV-Boost and validators 
Deliverable: Written report on 10 real MEV transactions you analyzed

Week 28-30: Arbitrage Theory
Daily Tasks:
    • Implement triangular arbitrage logic 
    • Calculate gas costs accurately 
    • Build profit calculation engine 
    • Paper trade opportunities 
Key Concepts:
    • Multi-hop swaps 
    • Gas optimization techniques 
    • Slippage tolerance 
    • MEV competition dynamics 
Deliverable: Arbitrage simulator (no real trading)

Week 31-33: Advanced Gas Optimization
Daily Tasks:
    • Study gas costs of different operations 
    • Learn about EIP-1559 
    • Implement dynamic gas pricing 
    • Build gas estimation tools 
Key Concepts:
    • Base fee vs priority fee 
    • Gas limits and out-of-gas errors 
    • Batching transactions 
    • Gas tokens (historical context) 
Deliverable: Gas optimization toolkit

Week 34-37: Keeper Architecture Patterns
Daily Tasks:
    • Study open-source keeper bots on GitHub 
    • Design state machine for opportunity detection 
    • Build monitoring + decision + execution pipeline 
    • Implement proper logging and alerting 
Architecture Components:
    • Event listener (websockets) 
    • Opportunity scanner 
    • Profitability calculator 
    • Transaction executor 
    • Database for state management 
    • Alerting system (Telegram/Discord) 
Deliverable: Generic keeper bot framework

Week 38-40: Domain-Specific Keeper
Choose ONE to build:
    1. Aave Liquidation Watcher - Monitor health factors 
    2. NFT Floor Price Monitor - Track listing opportunities 
    3. Stablecoin Depeg Monitor - Alert on significant deviations 
Requirements:
    • Real-time monitoring 
    • SQLite/PostgreSQL for tracking 
    • Notification system 
    • No actual trading (simulation only) 
Deliverable: Working keeper bot in your chosen domain (testnet)

🏆 PHASE 4: MakerDAO Liquidation Keeper (Weeks 41-56)
Goal: Build production-ready MakerDAO auction keeper
Week 41-44: MakerDAO Deep Dive
Daily Tasks:
    • Read MakerDAO whitepaper 
    • Study Vaults (Collateralized Debt Positions) 
    • Understand DAI peg mechanism 
    • Learn liquidation mechanics 
Key Concepts:
    • Collateralization ratios 
    • Liquidation penalty 
    • Auction mechanisms (Clipper for Collateral, Flapper for Surplus) 
    • Oracle price feeds 
    • Debt auctions vs surplus auctions 
Deliverable: Comprehensive notes document on MakerDAO architecture

Week 45-46: Historical Analysis
Daily Tasks:
    • Browse Etherscan for MakerDAO auction contracts 
    • Analyze past liquidation events 
    • Study successful keeper transactions 
    • Calculate historical profitability 
Contracts to Study:
    • Dog (Liquidation engine) 
    • Clipper (Collateral auctions) 
    • Vat (Core CDP engine) 
    • Spot (Price oracle) 
Deliverable: Spreadsheet analyzing 20+ historical auctions

Week 47-48: Testnet Setup
Daily Tasks:
    • Get testnet ETH (Goerli or Sepolia) 
    • Interact with MakerDAO testnet contracts 
    • Create test Vault 
    • Trigger test liquidation 
Key Concepts:
    • Testnet vs mainnet differences 
    • Faucets and test tokens 
    • Testnet explorers 
Deliverable: Successfully participated in testnet auction

Week 49-52: Auction Event Listener
Daily Tasks:
    • Build websocket listener for Kick events 
    • Parse auction parameters (lot, tab, top) 
    • Store auction data in database 
    • Build auction tracking dashboard 
Events to Monitor:
    • Kick - Auction started 
    • Take - Partial buy 
    • Redo - Auction reset 
Deliverable: Real-time auction monitor (testnet)

Week 53-54: Profitability Calculator
Daily Tasks:
    • Fetch current collateral prices 
    • Calculate bid profitability 
    • Account for gas costs 
    • Implement risk checks 
Calculation Formula:
Profit = (Collateral_Value - Bid_Cost) - Gas_Cost - Safety_Margin
Risk Checks:
    • Maximum bid per auction 
    • Maximum exposure per collateral type 
    • Gas price ceiling 
    • Slippage tolerance 
Deliverable: Profitability engine with unit tests

Week 55: Bid Executor
Daily Tasks:
    • Build transaction signing module 
    • Implement nonce management 
    • Add transaction monitoring 
    • Handle failed transactions gracefully 
Safety Features:
    • Dry-run mode 
    • Manual approval option 
    • Emergency stop mechanism 
    • Maximum daily loss limit 
Deliverable: Safe bid execution module

Week 56: Integration & Testing
Daily Tasks:
    • Connect all components 
    • Run end-to-end tests on testnet 
    • Simulate various auction scenarios 
    • Build monitoring dashboard 
Full System Components:
    1. Event Listener → detects auctions 
    2. Profitability Calculator → evaluates opportunities 
    3. Bid Executor → submits transactions 
    4. Database → tracks state and history 
    5. Dashboard → Flask UI for monitoring 
    6. Alerting → Telegram notifications 
Deliverable: Complete keeper bot running on testnet

🔄 BUFFER PHASE (Weeks 57-60)
Goal: Prepare for mainnet and refine strategy
Week 57-58: Code Review & Optimization
    • Refactor code for readability 
    • Improve error handling 
    • Optimize database queries 
    • Add comprehensive logging 
    • Security audit your code 
Week 59: Capital Planning
    • Calculate required capital 
    • Estimate monthly gas costs 
    • Plan for collateral diversity 
    • Set profit targets 
    • Risk management strategy 
Week 60: Mainnet Preparation
    • Set up mainnet RPC (paid tier) 
    • Fund mainnet wallet with ETH 
    • Configure production environment 
    • Set conservative risk parameters 
    • Start with small test bids 

📊 Timeline Summary
Phase
Weeks
Focus
Key Milestone
Phase 1
1-10
Foundations
Wallet Watcher API deployed
Phase 2
11-24
Automation
DEX Price Monitor live
Phase 3
25-40
Keeper Mindset
Domain-specific keeper bot
Phase 4
41-56
MakerDAO Keeper
Testnet keeper operational
Buffer
57-60
Refinement
Mainnet-ready
Total Time: 14-16 months at 1-2 hours/day

💰 Realistic Earnings Timeline
    • Months 1-6: $0 (learning phase) 
    • Months 7-12: $0-100 (small testnet experiments) 
    • Months 13-16: $0-500/month (initial mainnet testing, mostly covering costs) 
    • Months 17+: Variable ($500-5000+/month possible, but competition is intense) 
Reality Check: Modern keeper bots compete with sophisticated MEV searchers. Your first 6 months on mainnet will likely be break-even or slightly negative as you learn and optimize.

🎓 Learning Resources
Essential Reading
    • Ethereum.org documentation 
    • MakerDAO Developer Docs 
    • Flashbots documentation 
    • "How to DeFi" book series 
GitHub Repos to Study
    • Official MakerDAO keeper implementations 
    • Uniswap V2/V3 SDKs 
    • Web3.py examples 
    • Keeper bot templates 
Communities
    • MakerDAO Discord/Forum 
    • Ethereum StackExchange 
    • r/ethdev 
    • BuilderDAO Discord 

⚠️ Critical Success Factors
    1. Consistency - The 1-2 hours daily matters more than occasional long sessions 
    2. Documentation - Keep detailed notes of what you learn 
    3. Testing - Never skip writing tests, especially for financial code 
    4. Security - Treat every private key like it holds $1M 
    5. Community - Join Discord servers, ask questions, share progress 
    6. Patience - Profits won't come immediately; treat first year as education 

🚀 Next Steps
Week 1 Starts Now:
    1. Install Python 3.10+ 
    2. Create GitHub account 
    3. Install Git 
    4. Create your first repository 
    5. Sign up for Alchemy/Infura 
Track Your Progress:
    • Commit code daily 
    • Write weekly reflection notes 
    • Build in public (tweet/blog about learning) 
    • Join one Web3 developer community 

📝 Final Notes
This curriculum is ambitious but achievable. You have the foundational skills (Python, Flask, Linux) that many aspiring Web3 developers lack.
The key differentiator will be your ability to:
    • Persist through challenging concepts (MEV, gas optimization) 
    • Test thoroughly before risking real capital 
    • Learn from failures (lost opportunities, bad bids) 
    • Stay current with protocol changes 
Your advantage: You're building this skill systematically over 12+ months rather than rushing in. Most failed keeper operators skip the fundamentals.
Good luck! 🎯


## Goals
- Master Web3 development
- Build decentralized applications
- Contribute to blockchain ecosystem
