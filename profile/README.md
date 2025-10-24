# 🌉 Nusa Protocol

<div align="center">

![Nusa Logo](https://miniapp.nusa.io/splash.png)

**A Cross-Chain Local Stablecoin Lending Hub — Built for Farcaster, Powered by LayerZero.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Next.js](https://img.shields.io/badge/Next.js-15.5.4-black?style=for-the-badge\&logo=next.js)](https://nextjs.org/)
[![Solidity](https://img.shields.io/badge/Solidity-^0.8.20-blue?style=for-the-badge\&logo=solidity)](https://soliditylang.org/)
[![LayerZero](https://img.shields.io/badge/LayerZero-V2-purple?style=for-the-badge)](https://layerzero.network/)
[![Ponder](https://img.shields.io/badge/Indexer-Ponder-green?style=for-the-badge)](https://ponder.sh/)
[![Farcaster](https://img.shields.io/badge/Farcaster-Mini%20App-purple?style=for-the-badge)](https://farcaster.xyz/)

</div>

---

## 🚀 Overview

**Nusa Protocol** is a decentralized, cross-chain **local stablecoin lending hub** built to empower users across the world to **lend and borrow stablecoins backed by Real World Assets (RWA)** — all natively integrated within the **Farcaster** ecosystem.

Our stack combines:

* **Frontend Mini App** — an interactive Farcaster app built with Next.js.
* **Smart Contracts** — the cross-chain lending engine powered by LayerZero V2.
* **Indexer** — real-time on-chain data aggregation for analytics and UI.

---

## 🧩 Architecture Overview

```
├── nusa-fe/       # Frontend (Next.js Farcaster Mini App)
├── nusa-sc/       # Smart Contracts (Solidity + Foundry)
└── nusa-indexer/  # Data Indexer (Ponder + PostgreSQL)
```

Each subproject can run independently, but together they form the full **Nusa Lending Protocol**.

---

## 🌐 Core Components

### 1️⃣ Frontend – `nusa-fe`

**Tech Stack**

* Framework: **Next.js 15** (App Router)
* Language: **TypeScript**
* UI: **Tailwind CSS**, **Framer Motion**, **GSAP**
* Web3: **Wagmi**, **Viem**, **RainbowKit**
* Farcaster SDK: **MiniApp SDK v0.2.0**

**Highlights**

* Native Farcaster Mini App experience
* Smooth GSAP animations & responsive UI
* Wallet integration via RainbowKit
* Real-time market and portfolio tracking
* Supports **Base**, **Arbitrum**, **Ethereum**, **Optimism**, **BNB Chain**

👉 **Repo:** [nusa-fe](https://github.com/nusa-finance/nusa-fe)

---

### 2️⃣ Smart Contracts – `nusa-sc`

**Tech Stack**

* Language: **Solidity (v0.8.20)**
* Framework: **Foundry**
* Cross-chain: **LayerZero V2 OApp**
* Libraries: **OpenZeppelin**, **Forge Std**

**Key Features**

* Cross-chain borrowing (LayerZero OApp)
* Dynamic interest rate model
* Configurable LTV & liquidation thresholds
* Role-based governance and pausability
* Oracle-based RWA price feeds
* Fully upgradeable via UUPS proxy pattern

**Core Contracts**

| Contract              | Description                            |
| --------------------- | -------------------------------------- |
| `LendingPool.sol`     | Core lending and collateral management |
| `L0/OAppBorrow.sol`   | LayerZero cross-chain borrow messaging |
| `Router.sol`          | Cross-chain asset mapping              |
| `TokenDataStream.sol` | Oracle price feed integration          |

**Supported Networks**

* **Base** (Chain ID: 8453)
* **Arbitrum** (Chain ID: 42161)
* **Local Testnet** (Chain ID: 999)

👉 **Repo:** [nusa-sc](https://github.com/nusa-finance/nusa-sc)

---

### 3️⃣ Indexer – `nusa-indexer`

**Tech Stack**

* Framework: **Ponder**
* Database: **PostgreSQL**
* Language: **TypeScript**
* RPCs: **Base / Arbitrum RPC endpoints**

**Responsibilities**

* Indexes on-chain events from lending and oracle contracts
* Aggregates protocol data (TVL, rates, health factors)
* Exposes REST & GraphQL endpoints for UI and analytics

**Key Entities**

| Entity                 | Description                          |
| ---------------------- | ------------------------------------ |
| `markets`              | Supply/borrow stats per market       |
| `tokens`               | Metadata, thresholds, oracle sources |
| `positions`            | User portfolio, collaterals, debts   |
| `oracle_prices`        | Latest RWA & stablecoin prices       |
| `protocol_stats_daily` | Daily TVL, revenue, fees             |
| `cross_chain_messages` | LayerZero OApp message logs          |

👉 **Repo:** [nusa-indexer](https://github.com/nusa-finance/nusa-indexer)

---

## 💎 Supported Assets

### 💰 Local Stablecoins

| Symbol | Currency           |
| ------ | ------------------ |
| CADC   | Canadian Dollar    |
| CNGN   | Chinese Yuan       |
| KRWT   | Korean Won         |
| TRYB   | Turkish Lira       |
| MXNE   | Mexican Peso       |
| XSGD   | Singapore Dollar   |
| ZARP   | South African Rand |
| IDRX   | Indonesian Rupiah  |
| EURC   | Euro Coin          |

### 🏢 Real World Assets (RWA)

| Symbol | Description                |
| ------ | -------------------------- |
| bCOIN  | Bitcoin RWA Token          |
| bCSPX  | S&P 500 RWA Token          |
| bTSLA  | Tesla RWA Token            |
| bGOOGL | Google RWA Token           |
| bNVDA  | NVIDIA RWA Token           |
| bMSFT  | Microsoft RWA Token        |
| bGME   | GameStop RWA Token         |
| bIB01  | iShares Bond RWA Token     |
| bIBTA  | iShares Treasury RWA Token |
| bHIGH  | High Yield RWA Token       |
| bZPR1  | ZPR1 RWA Token             |

---

## 🛠️ Development Guide

### Requirements

* Node.js 18+
* Foundry
* PostgreSQL 14+
* pnpm / yarn / npm
* Git

### Local Setup

```bash
# Clone the full org monorepo
git clone https://github.com/nusa-finance/nusa-protocol.git
cd nusa-protocol

# Navigate to any module
cd nusa-fe      # Frontend
cd nusa-sc      # Smart Contracts
cd nusa-indexer # Indexer
```

Follow each module’s individual README for detailed setup.

---

## 🔒 Security & Audits

* Built with **OpenZeppelin** audited libraries
* Cross-chain messaging via **LayerZero V2 (OApp)**
* Health monitoring and liquidation safeguards
* Smart contract audits scheduled prior to mainnet launch
* Wallet connection secured via **RainbowKit**

---

## 📊 Monitoring & Analytics

* **TVL, utilization, borrow rates** tracked by indexer
* **Health factor monitoring** for all positions
* **Cross-chain latency** via `cross_chain_messages` table
* **GraphQL API** for custom dashboards or data pipelines

---

## 📄 License

This project is licensed under the **MIT License** — see [LICENSE](LICENSE) for details.

---

## 🔗 Links

* 🌐 **Live Mini App:** [Launch on Farcaster](https://farcaster.xyz/miniapps/CwB--wdey8nn/nusa)
* 💬 **Telegram:** [Nusa Finance Indonesia](https://t.me/NusaFinanceIndonesia)
* 🐦 **Twitter/X:** [@nusa_finance](https://x.com/nusa_finance)
* 💻 **Discord:** [Join our community](https://discord.gg/ZDJXXzhN8c)
* 📚 **LayerZero Docs:** [docs.layerzero.network/v2](https://docs.layerzero.network/v2)

---

<div align="center">

**Built with ❤️ by the Nusa Protocol Team**
Empowering global DeFi through local stablecoins.

</div>
