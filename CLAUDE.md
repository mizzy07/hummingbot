# Hummingbot Development Guide

## Project Overview

Hummingbot is an open-source framework for designing and deploying automated trading strategies (bots) on centralized and decentralized exchanges. The project enables algorithmic traders and developers to build sophisticated trading strategies that can run across 140+ unique trading venues.

**Key Facts:**
- Open-source under Apache 2.0 license
- Users have generated $34+ billion in trading volume
- Mission: Democratize high-frequency trading through community contributions
- Supports both CLI-based client and web-based Dashboard

## Exchange Connector Types

Hummingbot supports three main connector categories:

1. **CLOB CEX**: Centralized exchanges with order books (Spot & Perpetual)
   - Examples: Binance, KuCoin, OKX, Coinbase

2. **CLOB DEX**: Decentralized exchanges with on-chain order books (non-custodial)
   - Examples: dYdX, Hyperliquid, Derive

3. **AMM DEX**: Automated Market Maker decentralized exchanges (via Gateway middleware)
   - Examples: Uniswap, Curve, Balancer, PancakeSwap

## Key Directories

```
hummingbot/
├── gateway-files/          # Gateway DEX middleware configuration
├── certs/                  # Certificate files for Gateway
├── CONTRIBUTING.md         # Contribution guidelines
├── LICENSE                 # Apache 2.0 license
├── docker-compose.yml      # Docker setup for local development
└── README.md              # Main documentation
```

## Development Setup

### Prerequisites
- Docker and Docker Compose installed

### Quick Start with Docker

```bash
# Clone the repository
git clone https://github.com/hummingbot/hummingbot.git
cd hummingbot

# Launch Hummingbot
docker compose up -d

# Attach to the running instance
docker attach hummingbot
```

### Setup with Gateway (DEX support)

1. Clone the repository
2. Uncomment Gateway service lines in `docker-compose.yml`
3. Configure environment variables (GATEWAY_PASSPHRASE, DEV flag)
4. Run: `docker compose up -d`

**Note:** Gateway defaults to development mode (unencrypted HTTP). Set `DEV=false` and run `gateway generate-certs` for production with HTTPS.

### Install from Source

For building new connectors, strategies, or adding custom code:
- See: [Install from Source](https://hummingbot.org/installation/source/)

## Common Commands

### Docker Operations
```bash
docker compose up -d              # Start services in background
docker attach hummingbot           # Connect to running instance
docker compose down                # Stop all services
```

### Gateway Operations
```bash
gateway generate-certs             # Generate certificates for HTTPS (production mode)
```

### Development
```bash
# Submit contributions following guidelines in CONTRIBUTING.md
# New connector proposals require HBOT tokens in Ethereum wallet
```

## Resources

- **Official Docs**: https://hummingbot.org
- **Discord Community**: https://discord.gg/hummingbot
- **GitHub Issues**: Report bugs or suggest features
- **FAQ & Troubleshooting**: https://hummingbot.org/faq/

## Related Repositories

- **Deploy**: Docker configurations for various setups
- **Dashboard**: Web UI for creating, backtesting, and managing bots
- **Quants Lab**: Jupyter notebooks for research and data fetching
- **Gateway**: TypeScript API client for DEX connectors
- **Hummingbot Site**: Official documentation repository

## Contributing

- Review [CONTRIBUTING.md](./CONTRIBUTING.md) before submitting PRs
- Follow [governance guidelines](https://hummingbot.org/governance/proposals/) for new connectors
- Community members maintain modular components independently
