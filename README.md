# GiftDrop 🎁

> Friends secretly drop money for someone's gift — reveals automatically on the special day.

GiftDrop is a web app built on Stellar where friends can secretly pool money for someone's
birthday, farewell, or special occasion. Built with Soroban smart contracts on Stellar testnet.

## 🔗 Links
- **Live Demo**: https://giftdrop-five.vercel.app
- **Demo Video**: https://drive.google.com/file/d/1C5Jg7teBDdf74l01LYgONaiqICeRPkbM/view?usp=drive_link
- **User Feedback**: https://docs.google.com/forms/d/1bAluxRpwHa0V83twN_V0JHLjGgYTgAtQEcsk4uCYMXU/edit#responses
- **Smart Contract**: `CCKWQPTEXUAV7RK3WKD2T6YS4CLC4QE2KWI2MO4NHVAN4ABFJHA3YGVJ`
- **Contract Explorer**: [View on Stellar Expert](https://stellar.expert/explorer/testnet/contract/CCKWQPTEXUAV7RK3WKD2T6YS4CLC4QE2KWI2MO4NHVAN4ABFJHA3YGVJ)

## ✨ What is GiftDrop?

GiftDrop solves a real problem — when a group of friends wants to pool money for a surprise
gift, someone always has to be trusted with the funds and manually collect from everyone.
GiftDrop eliminates this by locking funds in a Soroban smart contract that automatically
releases on the reveal date, or refunds everyone if the target isn't met.

## 🎯 Real-world Use Cases
- Birthday surprise gifts
- Farewell gifts for colleagues
- Festival group gifting
- Office celebration pools

## ✨ Features
- **Create a Gift Drop** — Set target amount, recipient wallet, deadline and reveal date
- **Secret Contributions** — Friends lock XLM silently into smart contract
- **Hidden from Recipient** — Recipient can't see amount or contributors until reveal date
- **Auto Release** — Full amount releases to recipient on reveal date
- **Auto Refund** — Everyone gets refunded if target isn't met by deadline
- **No Trust Needed** — Smart contract handles everything, no manual collection
- **Explorer Links** — Every transaction visible on Stellar Expert

## 👥 Testnet Users
The following wallet addresses have tested GiftDrop on Stellar testnet:

| User | Wallet Address |
|------|---------------|
| User 1 | `GDBIJAOFPMGQWDUUQTJ3YFHI44MWHQHPALJQG7ZDA7D5WWEDKJYA4OHA` |
| User 2 | `GBLUMAX4IIPS54AIGD5WXRRAXISG4HLV3BE3YR3SQAD3GZSXRTVJY5GI` |
| User 3 | `GAHWHBKOQRUF3NY5BLRAFPEBWMN2RAAB73F3IPSGIRRIRX6CZ3PERSCH` |
| User 4 | `GDJ6VJX3OVJJLIF2J2JRBBDD6PYAZNLAMJIDOLJQSWTUCGDSKEBOEOFP` |
| User 5 | `GACPV4RIAZ3VWN7LKZVTPLABOWBGAZUH3PVUJ5OX6PJ4TO3PNVABSR56` |
| User 6 | `GCSX7FR6XYMAPHEJASF2RA3BHQV3PM4DKVW3FTSQV76IIR7GYIGJSW3W` |

## 🏗️ Architecture
```
User Browser
     ↓
Next.js Frontend (Vercel)
     ↓
@stellar/stellar-sdk
     ↓
Soroban RPC (soroban-testnet.stellar.org)
     ↓
Soroban Smart Contract (Rust)
     ↓
Stellar Testnet Blockchain
```

## 📋 Smart Contract Functions

| Function | Description |
|----------|-------------|
| `create_gift` | Creates a new gift drop on-chain |
| `contribute` | Locks XLM contribution on-chain |
| `get_gift` | Fetches gift drop details |
| `get_contributors` | Returns all contributors for a drop |
| `get_organizer_gifts` | Returns all drops created by organiser |
| `get_contributor_gifts` | Returns all drops contributed to |
| `reveal` | Releases funds to recipient on reveal date |
| `refund` | Refunds contributors if target not met |

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | Next.js + TypeScript |
| Blockchain | Stellar Testnet |
| Smart Contract | Soroban (Rust) |
| Wallet | Freighter |
| Deployment | Vercel |
| Stellar SDK | @stellar/stellar-sdk |

## 📁 Project Structure
```
giftdrop/
├── contracts/
│   └── gift_drop/
│       ├── Cargo.toml
│       └── src/
│           └── lib.rs          # Soroban smart contract (Rust)
├── frontend/
│   ├── app/
│   │   ├── create/             # Create gift drop page
│   │   ├── dashboard/          # My drops and contributions
│   │   ├── drop/               # Individual drop page
│   │   └── reveal/             # Reveal page
│   ├── lib/
│   │   ├── contract.ts         # All blockchain interactions
│   │   └── stellar.ts          # Stellar SDK helpers
│   └── components/             # Reusable UI components
├── README.md
└── ARCHITECTURE.md
```

## 🚀 Installation
```bash
# Clone the repository
git clone https://github.com/vaiii05-hub/Stellar-Internship-Level-5.git
cd Stellar-Internship-Level-5/frontend

# Install dependencies
npm install

# Run locally
npm run dev
```

## ⚙️ Environment Setup

Create `.env.local` in the frontend folder:
```
NEXT_PUBLIC_GIFT_DROP_CONTRACT=CCKWQPTEXUAV7RK3WKD2T6YS4CLC4QE2KWI2MO4NHVAN4ABFJHA3YGVJ
NEXT_PUBLIC_DEPLOYER_ADDRESS=your_deployer_address
```

## 👛 Wallet Setup for Users

1. Install **Freighter** browser extension
2. Create a new wallet
3. Switch network to **Testnet**
4. Get free testnet XLM from [Friendbot](https://friendbot.stellar.org)
5. Visit https://giftdrop-five.vercel.app and connect!

## 📝 User Feedback

Feedback collected from 6 testnet users via Google Form.

👉 [View Feedback Responses](https://docs.google.com/forms/d/1bAluxRpwHa0V83twN_V0JHLjGgYTgAtQEcsk4uCYMXU/edit#responses)

## 🔄 Iterations Completed

- **Fixed expired drops disappearing** — Added null safety so expired drops show
  with "Expired" status badge instead of vanishing from dashboard
- **Added transaction confirmation** — Contributors now see Stellar Explorer link
  after contributing so they can verify on-chain

## 🔍 Verify on Stellar Explorer

- **Contract**: [`CCKWQP...3YGVJ`](https://stellar.expert/explorer/testnet/contract/CCKWQPTEXUAV7RK3WKD2T6YS4CLC4QE2KWI2MO4NHVAN4ABFJHA3YGVJ)
- All transactions visible on Stellar Expert Testnet

## 📄 License

MIT License — feel free to use and build on this project.
