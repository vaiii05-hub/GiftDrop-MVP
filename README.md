# 🎁 GiftDrop

> **Friends secretly pool money for someone's gift — reveals automatically on the special day.**

GiftDrop is a decentralized group gifting platform built on Stellar, powered by Soroban smart contracts. Friends can silently contribute XLM toward a shared gift, with funds locked on-chain and automatically released to the recipient on the reveal date — or refunded to everyone if the target isn't met.

---

## 🔗 Quick Links

| Resource | Link |
|----------|------|
| 🌐 Live Demo | https://giftdrop-five.vercel.app |
| 🎥 Demo Video | [Watch on Google Drive](https://drive.google.com/file/d/1C5Jg7teBDdf74l01LYgONaiqICeRPkbM/view?usp=drive_link) |
| 📊 Metrics Dashboard | https://giftdrop-five.vercel.app/metrics |
| 🔍 Smart Contract | [View on Stellar Expert](https://stellar.expert/explorer/testnet/contract/CCKWQPTEXUAV7RK3WKD2T6YS4CLC4QE2KWI2MO4NHVAN4ABFJHA3YGVJ) |
| 🐦 Community Post | [Twitter/X Post](https://x.com/vaiii05/status/2037897578281644247?s=20) |
| 📋 User Feedback | [32 Responses — Google Form](https://docs.google.com/forms/d/1f3dUDnkxFBX7WskQIENhjcNaXxdSotH63lhPnMW5EXM/edit#responses) |
| 🔒 Security Checklist | [View SECURITY.md](./SECURITY.md) |
| 📖 User Guide | [View USER_GUIDE.md](./USER_GUIDE.md) |
| 📐 Architecture Docs | [View ARCHITECTURE.md](./ARCHITECTURE.md) |

**Smart Contract Address:**
```
CCKWQPTEXUAV7RK3WKD2T6YS4CLC4QE2KWI2MO4NHVAN4ABFJHA3YGVJ
```

---

## 📌 Table of Contents

1. [Problem Statement](#-problem-statement)
2. [What is GiftDrop?](#-what-is-giftdrop)
3. [Features](#-features)
4. [Tech Stack](#-tech-stack)
5. [Architecture](#-architecture)
6. [Smart Contract Functions](#-smart-contract-functions)
7. [Advanced Feature — Fee Sponsorship](#-advanced-feature--fee-sponsorship)
8. [Metrics Dashboard](#-metrics-dashboard)
9. [Monitoring](#-monitoring)
10. [Data Indexing](#-data-indexing)
11. [Security Checklist](#-security-checklist)
12. [Community Contribution](#-community-contribution)
13. [User Feedback & Improvements](#-user-feedback--improvements)
14. [Future Roadmap](#-future-roadmap)
15. [Testnet Users (32)](#-testnet-users-32)
16. [Installation & Setup](#-installation--setup)
17. [Wallet Setup](#-wallet-setup-for-users)

---

## 💡 Problem Statement

When a group of friends wants to pool money for a surprise gift, someone always has to be trusted with the funds — manually chasing people, collecting cash, and managing the entire process. This creates friction, trust issues, and often ruins the surprise.

**GiftDrop eliminates this entirely.** No coordinator needed. No trust required. The smart contract handles everything.

---

## 🎁 What is GiftDrop?

GiftDrop is a Web3 group gifting app on Stellar Testnet where:

- An **organizer** creates a Gift Drop with a target amount, recipient wallet, deadline, and reveal date
- **Friends** silently contribute XLM — all locked on-chain, invisible to the recipient
- On the **reveal date**, the full amount automatically releases to the recipient
- If the **target isn't met** by the deadline, everyone gets a full refund automatically

No middleman. No trust. Just code.

---

## 🎯 Real-World Use Cases

- 🎂 Birthday surprise gifts
- 👋 Farewell gifts for colleagues
- 🎉 Festival group gifting
- 🏢 Office celebration pools

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| 🎁 Create a Gift Drop | Set target amount, recipient wallet, deadline, and reveal date |
| 🤫 Secret Contributions | Friends lock XLM silently into the smart contract |
| 👁️ Hidden from Recipient | Recipient cannot see amount or contributors until reveal date |
| ⚡ Auto Release | Full amount releases to recipient on reveal date |
| 🔄 Auto Refund | Everyone is refunded if target isn't met by deadline |
| 🔒 No Trust Needed | Smart contract handles everything — no manual collection |
| 🔍 Explorer Links | Every transaction visible on Stellar Expert |
| ⛽ Fee Sponsorship | Gasless transactions via Stellar fee bump |
| 📊 Metrics Dashboard | Live on-chain metrics and full transaction history |
| 🧭 Metrics in Navbar | Metrics page accessible directly from the navigation bar |
| 🚦 Contribution Limit | Max contribution per user enforced on-chain to ensure fair participation |

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|------------|
| Frontend | Next.js + TypeScript |
| Blockchain | Stellar Testnet |
| Smart Contract | Soroban (Rust) |
| Wallet | Freighter Browser Extension |
| Deployment | Vercel |
| Stellar SDK | @stellar/stellar-sdk |
| Monitoring | Custom Logger (`frontend/lib/logger.ts`) + Vercel Logs |
| Data Indexing | Stellar Horizon API |

---

## 🏗️ Architecture

```
User Browser
     │
     ▼
Next.js Frontend (Vercel)
     │
     ▼
@stellar/stellar-sdk
     │
     ▼
Soroban RPC (soroban-testnet.stellar.org)
     │
     ▼
Soroban Smart Contract (Rust)
     │
     ▼
Stellar Testnet Blockchain
```

---

## 📋 Smart Contract Functions

| Function | Description |
|----------|-------------|
| `create_gift` | Creates a new gift drop on-chain |
| `contribute` | Locks XLM contribution on-chain (subject to per-user contribution limit) |
| `get_gift` | Fetches gift drop details |
| `get_contributors` | Returns all contributors for a drop |
| `get_organizer_gifts` | Returns all drops created by organizer |
| `get_contributor_gifts` | Returns all drops contributed to |
| `reveal` | Releases funds to recipient on reveal date |
| `refund` | Refunds contributors if target not met |

---

## ⚡ Advanced Feature — Fee Sponsorship

GiftDrop implements **gasless transactions** using Stellar fee bump transactions. Contributors do not need XLM for gas fees — a sponsor account covers fees on their behalf.

**Implementation file:** `frontend/lib/contract.ts` → `contributeWithFeeSponsor()`

**How it works:**

1. Sponsor account wraps the contributor's inner transaction
2. Fee bump transaction covers all gas fees
3. Contributor signs and submits without needing XLM for fees

This dramatically lowers the barrier to entry for new users — they only need XLM for their actual contribution, not for network fees.

---

## 📊 Metrics Dashboard

**Live URL:** https://giftdrop-five.vercel.app/metrics

The Metrics page is accessible directly from the **navigation bar** (added as part of recent improvements). It displays real-time on-chain data pulled from Stellar Testnet:

- Total transactions on the contract
- Network (Stellar Testnet)
- Smart contract address with direct Explorer link
- Full on-chain transaction history with hashes, types, dates, and individual Explorer links

**Screenshot:**

![GiftDrop Metrics Dashboard](<img width="1920" height="1080" alt="Screenshot 2026-03-31 215854" src="https://github.com/user-attachments/assets/ee40d987-b79b-49b1-8903-37904bcee3c5" />


> *19 on-chain transactions as of March 30, 2026 — all verifiable on Stellar Expert.*

---

## 📡 Monitoring

GiftDrop uses a **custom logger** (`frontend/lib/logger.ts`) that logs all key application events with structured `[GiftDrop INFO]` prefixed messages. These are visible in the browser console and captured in Vercel deployment logs.

**Screenshot:**

![GiftDrop Monitoring — Console Logger](<img width="1920" height="1080" alt="Screenshot 2026-03-28 201948" src="https://github.com/user-attachments/assets/89840691-02ac-4ad2-8426-ce4a81759412" />
)

> *Console showing `[GiftDrop INFO] GiftDrop app loaded` — custom logger fires on every app load, confirming monitoring is active.*

**Monitoring stack:**
- Custom logger: `frontend/lib/logger.ts`
- Vercel deployment logs: Available in Vercel dashboard under the GiftDrop project
- On-chain transaction explorer: [Stellar Expert — Contract Transactions](https://stellar.expert/explorer/testnet/contract/CCKWQPTEXUAV7RK3WKD2T6YS4CLC4QE2KWI2MO4NHVAN4ABFJHA3YGVJ)

---

## 📈 Data Indexing

GiftDrop uses the **Stellar Horizon API** to index and display all on-chain transactions in the Metrics Dashboard.

**Indexing Endpoint:**
```
https://horizon-testnet.stellar.org/accounts/CCKWQPTEXUAV7RK3WKD2T6YS4CLC4QE2KWI2MO4NHVAN4ABFJHA3YGVJ/transactions
```

**What is indexed:**
- All contract call transactions
- Transaction hashes and timestamps
- Contributor and organizer activity
- Live metrics: total transactions, total XLM contributed, active users

---

## 🔒 Security Checklist

A complete security review has been conducted and documented.

👉 [View Full Security Checklist — SECURITY.md](./SECURITY.md)

Key areas covered:
- Smart contract access controls
- Fund locking and release logic
- Contribution limit enforcement (max per user)
- Refund protection
- Frontend input validation
- Wallet connection safety

---

## 🐦 Community Contribution

GiftDrop was shared with the Stellar developer and user community on Twitter/X to spread awareness and onboard testnet users.

👉 [View Twitter/X Post](https://x.com/vaiii05/status/2037897578281644247?s=20)

---

## 📝 User Feedback & Improvements

Feedback was collected from **32 testnet users** via Google Form.

👉 [View All 32 Responses](https://docs.google.com/forms/d/1f3dUDnkxFBX7WskQIENhjcNaXxdSotH63lhPnMW5EXM/edit#responses)

### Implemented Improvements

| # | User Feedback | Improvement Made |
|---|---------------|-----------------|
| 1 | "My old drops were disappearing from the dashboard" | Fixed expired drops — added null safety so expired drops show with an "Expired" status badge |
| 2 | "I had no way to verify if my contribution went through on blockchain" | Added transaction confirmation — contributors now see a Stellar Explorer link after contributing |
| 3 | "I didn't know what would happen if the target amount wasn't reached" | Added clear auto-refund message on the drop detail page |
| 4 | "I didn't know how much was raised compared to the target" | Added a progress bar showing percentage raised on each drop card |
| 5 | "I wanted to see my contributions separately from drops I created" | Added two separate tabs — My Drops and My Contributions on the dashboard |
| 6 | "Hard to find the metrics page" | Added Metrics link directly to the navigation bar for easy access |
| 7 | "Some users were contributing too much, leaving less room for others" | Implemented per-user max contribution limit enforced on-chain |

---

## 🔮 Future Roadmap

Based on feedback from 32 testnet users:

| # | Improvement | Plan |
|---|-------------|------|
| 1 | Mobile wallet support | Integrate LOBSTR mobile wallet |
| 2 | Email notifications | Notify contributors when reveal date approaches |
| 3 | Multiple token support | Allow USDC contributions alongside XLM |
| 4 | Social sharing | One-click share drop link to WhatsApp/Telegram |
| 5 | Gift messages | Allow contributors to add anonymous messages |

---

## 👥 Testnet Users (32)

32 real users have tested GiftDrop on Stellar Testnet. All wallet addresses are verifiable on [Stellar Expert Testnet Explorer](https://stellar.expert/explorer/testnet).

| # | Wallet Address |
|---|---------------|
| User 1 | `GCY335MWXOTIDG3JVLER2FSQ3LOFWIYUAZIDTCFAPFTXIOZ64CGLKUB5` |
| User 2 | `GBLUMAX4IIPS54AIGD5WXRRAXISG4HLV3BE3YR3SQAD3GZSXRTVJY5GI` |
| User 3 | `GCXY4DOI4DOJOVISJSXCLXL25QF5SWK3JG4BIURXVNTCV2IFWNEHM2J` |
| User 4 | `GCLTDFYMDJZYLDKETB6Z24CCPHGFQS7NRZFJWT4AUXQZ5SF2BJOME7CN` |
| User 5 | `GDJ6VJX3OVJJLIF2J2JRBBDD6PYAZNLAMJIDOLJQSWTUCGDSKEBOEOFP` |
| User 6 | `GARGMJJCMNGYHZPHPS47NANURZVT6EQIW2NDCE6PUFIC3YRCMDRBUDGD` |
| User 7 | `GDGAG234U66W25HS6EN4OYTD7RZWUKGMF5JGH5EWW46UEJTE7YUCJJTU` |
| User 8 | `GAGBXPGIVLCKAYRIAT3HMEXH7J2YMNO4WUGMNZW5DIN4MDXFTD246QHQ` |
| User 9 | `GBJ7S6KJYTGYY6COIUHRAH3INJXUTUJXG4EATKH6M6OE2ZC23WVWD4ZJ` |
| User 10 | `GAHFDM4MHIGKWNZERUH4GC5IMZAFN4IH7PZFJ6RAIKLZ2H356ITDSTGL` |
| User 11 | `GAEXD3KCFE3CBWDGSNQ5A624AMH74B4ONAEEF2QRUWHX6SOTTAVUGKRV` |
| User 12 | `GBTOTIACAKIJACTH62RZQZSZJV6QIYFVPXLSAPNCSB6Q4IYMWEKIH55D` |
| User 13 | `GDZ2MUOTU45WYR4MA6IAR63OB6IU53QYGNYOAJPPJT6VBNQLSOQEZFE2` |
| User 14 | `GDNLRW65EWJAP2AJQO5G6F2VSNHFZJJAC3VZ2GCAO452T5ICEJMFUFPL` |
| User 15 | `GD32Y4KNZI7PNFO6FKRWZO7VTCHOXMNVR3EZYLEKJ6QYN4QC3X3JUMN4` |
| User 16 | `GAI2EC7HSJ4DCE5QHRFYO5MYA6EV3XJCIW7D66PWUH6VUYL4DWSVGNZ2` |
| User 17 | `GCWGFZTDGBDQPTMU3KHRYWNDMW4PZEEHRL2INAX7UIKQB7UW7LMEH73V` |
| User 18 | `GALWWEGHOMU5YODTZBVGPFP2OHCJH5VO3VKWNMW7ZNT6OECINVPQT7SQ` |
| User 19 | `GCRYPAQB3TFLQE727TA3R723QIEPTP5KCMP7OMH4HVXNLCEUKPD4AZJP` |
| User 20 | `GA5JVZLQAMAKQ4FVMV5XAX3EKHPIR2AHMH6FSNCWKTB664A7NMTT3NPH` |
| User 21 | `GBLUQBHZGX5PM2A6FX45L3ONQVL56RNEUJ2BUSYM47A5N3Z37VPJPQ2Y` |
| User 22 | `GBNPQXKGMVPBGJUT2VTKOMWNG2JAGBG7DDOH4XY6CCO55NTTV5UKL3EQ` |
| User 23 | `GBLPM5I4DCKOWWVUPXKF5XONZSD22ZF3GHNDHK6ZB7PSQLIPPINXNENC` |
| User 24 | `GAHHWA4EMBFHGXN42EYODCP24G7YMT7FSMBARQZNMSEIPGVQWBYCDFCY` |
| User 25 | `GBTCO5WSTBEMWTLI7CXNDMFHJV7NTIPIAHTPRRNW3LC5HDNZI6M5JAQCG` |
| User 26 | `GCFQGTT5JEPZDJHFT7AKA4AD5CFLH3LU6TZMSYNTNNS2JO7BKAOAEFZV` |
| User 27 | `GDNKE22S6C3D3PPRGBKHB7SSQEMEZFDEZ223MOYCW73TQGRGI2BPAIG4` |
| User 28 | `GDBIJAOFPMGQWDUUQTJ3YFHI44MWHQHPALJQG7ZDA7D5WWEDKJYA4OHA` |
| User 29 | `GAHWHBKOQRUF3NY5BLRAFPEBWMN2RAAB73F3IPSGIRRIRX6CZ3PERSCH` |
| User 30 | `GACPV4RIAZ3VWN7LKZVTPLABOWBGAZUH3PVUJ5OX6PJ4TO3PNVABSR56` |
| User 31 | `GCSX7FR6XYMAPHEJASF2RA3BHQV3PM4DKVW3FTSQV76IIR7GYIGJSW3W` |
| User 32 | `GBTOTIACAKIJACTH62RZQZSZJV6QIYFVPXLSAPNCSB6Q4IYMWEKIH55D` |

> All addresses are verifiable on [Stellar Expert Testnet](https://stellar.expert/explorer/testnet).

---

## 📁 Project Structure

```
giftdrop/
├── contracts/
│   └── gift_drop/
│       ├── Cargo.toml
│       └── src/
│           └── lib.rs              # Soroban smart contract (Rust)
├── frontend/
│   ├── app/
│   │   ├── create/                 # Create gift drop page
│   │   ├── dashboard/              # My drops and contributions (tabbed)
│   │   ├── drop/                   # Individual drop detail page
│   │   ├── reveal/                 # Reveal page
│   │   └── metrics/                # Metrics dashboard (linked in navbar)
│   ├── lib/
│   │   ├── contract.ts             # All blockchain interactions
│   │   ├── stellar.ts              # Stellar SDK helpers
│   │   └── logger.ts               # Monitoring and structured logging
│   └── components/                 # Reusable UI components
├── assets/
│   ├── metrics-dashboard.png       # Metrics dashboard screenshot
│   └── monitoring-console.png     # Monitoring console screenshot
├── SECURITY.md                     # Security checklist
├── USER_GUIDE.md                   # Full user guide
├── ARCHITECTURE.md                 # Architecture documentation
└── README.md
```

---

## 🚀 Installation & Setup

### Prerequisites
- Node.js 18+
- [Freighter Wallet](https://freighter.app) browser extension
- Stellar testnet account with XLM (free via Friendbot)

### Clone & Run

```bash
# Clone the repository
git clone https://github.com/vaiii05-hub/Stellar-Internship-Level-6.git
cd Stellar-Internship-Level-6/frontend

# Install dependencies
npm install

# Run locally
npm run dev
```

### Environment Variables

Create a `.env.local` file in the `frontend/` folder:

```env
NEXT_PUBLIC_GIFT_DROP_CONTRACT=CCKWQPTEXUAV7RK3WKD2T6YS4CLC4QE2KWI2MO4NHVAN4ABFJHA3YGVJ
NEXT_PUBLIC_DEPLOYER_ADDRESS=your_deployer_address
```

---

## 👛 Wallet Setup for Users

1. Install the **[Freighter](https://freighter.app)** browser extension
2. Create a new wallet and securely save your seed phrase
3. Switch the network to **Testnet** in Freighter settings
4. Get free testnet XLM from [Friendbot](https://friendbot.stellar.org)
5. Visit [https://giftdrop-five.vercel.app](https://giftdrop-five.vercel.app) and connect your wallet

---

## 🔍 Verify on Stellar Explorer

All GiftDrop transactions are fully transparent and verifiable on-chain:

- **Contract**: [`CCKWQP...3YGVJ`](https://stellar.expert/explorer/testnet/contract/CCKWQPTEXUAV7RK3WKD2T6YS4CLC4QE2KWI2MO4NHVAN4ABFJHA3YGVJ)
- **Network**: Stellar Testnet
- **Explorer**: [Stellar Expert Testnet](https://stellar.expert/explorer/testnet)

---

## 📄 License

MIT License — free to use, fork, and build upon.

---

*Built with ❤️ on Stellar by [@vaiii05](https://x.com/vaiii05)*
