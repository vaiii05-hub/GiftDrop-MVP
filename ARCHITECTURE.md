# GiftDrop — Architecture Document

## Overview
GiftDrop uses a Soroban smart contract on Stellar testnet to trustlessly lock and release
pooled XLM contributions for surprise gifts.

## System Flow
```
Organiser
   │
   ▼
Creates Gift Drop
(target amount, recipient wallet, reveal date)
   │
   ▼
Soroban Smart Contract deployed
   │
   ▼
Friends contribute XLM ──► XLM locked in contract
(hidden from recipient)
   │
   ├── Reveal date reached + target met?
   │         │
   │         ▼
   │   Full amount released to recipient wallet 🎁
   │
   └── Deadline passed + target NOT met?
             │
             ▼
       All contributors refunded automatically 🔄
```

## Components

### 1. Frontend (Next.js on Vercel)
- Create gift drop form
- Contribute XLM UI
- Countdown to reveal date
- Stellar Explorer links for transparency

### 2. Soroban Smart Contract (Rust)
- Stores: organiser, recipient, target amount, reveal date, contributions map
- Functions:
  - `create_gift()` — initialise drop
  - `contribute()` — lock XLM from contributor
  - `reveal()` — release to recipient if conditions met
  - `refund()` — return XLM if target not met

### 3. Stellar Testnet
- XLM as the native currency
- Freighter wallet for transaction signing
- Stellar Expert for public verification

## Key Design Decisions

| Decision | Reason |
|----------|--------|
| Soroban smart contract | Trustless — no one can access funds before reveal date |
| XLM locking | Prevents double-spend, ensures committed contributions |
| Auto-refund logic | Removes organiser burden of chasing payments |
| Reveal date on-chain | Tamper-proof, no organiser can manually trigger early |

## Contract Address
`CCKWQPTEXUAV7RK3WKD2T6YS4CLC4QE2KWI2MO4NHVAN4ABFJHA3YGVJ`

## Network
- Network: Stellar Testnet
- RPC: https://soroban-testnet.stellar.org
- Explorer: https://stellar.expert/explorer/testnet