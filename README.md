🎁 GiftDrop

Friends secretly drop money for someone's gift — reveals automatically on the special day.

GiftDrop is a decentralized group gifting platform built on the Stellar blockchain. Friends pool money for a surprise gift without anyone needing to be trusted with the funds. Contributions are locked in a Soroban smart contract and automatically released to the recipient on the reveal date — or refunded to everyone if the target isn't met.

🔗 Important Links
ResourceLink🌐 Live Demogiftdrop-five.vercel.app🎬 Demo VideoWatch on Google Drive📊 Metrics Dashboardgiftdrop-five.vercel.app/metrics🐦 Community PostTwitter/X Post📝 User Feedback FormGoogle Form📋 User Responses (32)View Responses🔍 Smart ContractCCKWQP...3YGVJ on Stellar Expert🔒 Security ChecklistSECURITY.md📖 User GuideUSER_GUIDE.md

✨ What Problem Does GiftDrop Solve?
When a group of friends wants to pool money for a surprise gift, the old way is painful — someone has to collect money manually, be trusted with the funds, and reveal everything at the right time. GiftDrop eliminates this entirely using a Soroban smart contract on Stellar:

No one person holds the funds
Contributions are secret until the reveal date
Funds release automatically — no manual action needed
Everyone gets refunded automatically if the target isn't met


🎯 Real-World Use Cases

Birthday surprise gifts
Farewell gifts for colleagues
Festival group gifting
Office celebration pools


✨ Features
FeatureDescription🎁 Create a Gift DropSet target amount, recipient wallet, deadline, and reveal date🔒 Secret ContributionsFriends lock XLM silently into the smart contract👁️ Hidden from RecipientRecipient can't see amount or contributors until reveal date⚡ Auto ReleaseFull amount releases to recipient on reveal date🔄 Auto RefundEveryone gets refunded automatically if target isn't met🤝 No Trust NeededSmart contract handles everything — no manual collection🔍 Explorer LinksEvery transaction visible and verifiable on Stellar Expert⛽ Fee SponsorshipGasless transactions via Stellar fee bump📊 Metrics DashboardLive on-chain metrics added via Metrics tab in navbar🚦 Contribution LimitMax contribution per user enforced to ensure fair participation

📊 Metrics Dashboard
Live: giftdrop-five.vercel.app/metrics
The Metrics page is accessible directly from the navbar. It displays real-time on-chain data pulled from the Soroban smart contract via the Stellar Horizon API:

Total drops created
Total XLM contributed
Total active users
Full on-chain transaction history with Stellar Explorer links

Screenshot
Show Image

The metrics dashboard shows 19 on-chain contract call transactions, live on Stellar Testnet, with each transaction hash linked to Stellar Expert for full verification.


📡 Monitoring
Error monitoring is implemented via a custom logger (frontend/lib/logger.ts). The logger emits structured [GiftDrop INFO] events to the browser console on every app load and transaction, and all transactions are cross-linked with Stellar Explorer for on-chain verification.
Screenshot
Show Image

The browser console confirms the custom logger is active, emitting [GiftDrop INFO] GiftDrop app loaded on startup. All transaction events are logged with their Stellar Explorer links.

Monitoring approach:

Custom structured logger: frontend/lib/logger.ts
All transactions emit log entries with blockchain confirmation links
Vercel deployment logs capture server-side errors
Stellar Explorer provides immutable on-chain audit trail


⚡ Advanced Feature — Fee Sponsorship (Gasless Transactions)
GiftDrop implements Stellar fee bump transactions so contributors don't need XLM to pay gas fees — the sponsor account covers it on their behalf.
Implementation: frontend/lib/contract.ts → contributeWithFeeSponsor()
How it works:

Contributor signs the inner transaction (no XLM needed for fees)
Sponsor account wraps it in a fee bump transaction
Fee bump transaction covers all gas fees
Contributor's contribution locks on-chain without them needing any extra XLM

This dramatically lowers the barrier to entry for new users on Stellar testnet.

🚦 Advanced Feature — Contribution Limit Per User
To ensure fair participation across all contributors, GiftDrop enforces a maximum contribution limit per user on each gift drop. This is validated at the smart contract level, preventing any single contributor from dominating a pool.
Implementation: Enforced in the contribute function within contracts/gift_drop/src/lib.rs
How it works:

Each gift drop has a configurable per-user contribution cap
The smart contract checks the user's existing contributions before accepting a new one
If the limit is exceeded, the transaction is rejected on-chain
UI surfaces a clear error message to the contributor


📈 Data Indexing
GiftDrop uses the Stellar Horizon API to index and display all on-chain transactions in real time.
Endpoint:
https://horizon-testnet.stellar.org/accounts/CCKWQPTEXUAV7RK3WKD2T6YS4CLC4QE2KWI2MO4NHVAN4ABFJHA3YGVJ/transactions
This endpoint is polled by the Metrics Dashboard to display all contract call transactions, their hashes, dates, and direct links to Stellar Expert. No third-party indexer is required — Horizon provides complete transaction history for the deployed contract.

🐦 Community Contribution
GiftDrop was shared with the Stellar community on Twitter/X to spread awareness and gather testnet users.
Post: twitter.com/vaiii05 — GiftDrop announcement

👥 Testnet Users (32 Verified)
All 32 users below have tested GiftDrop on Stellar Testnet. Wallet addresses are verifiable on Stellar Expert Testnet.
#Wallet Address1GCY335MWXOTIDG3JVLER2FSQ3LOFWIYUAZIDTCFAPFTXIOZ64CGLKUB52GBLUMAX4IIPS54AIGD5WXRRAXISG4HLV3BE3YR3SQAD3GZSXRTVJY5GI3GCXY4DOI4DOJOVISJSXCLXL25QF5SWK3JG4BIURXVNTCV2IFWNEHM2J4GCLTDFYMDJZYLDKETB6Z24CCPHGFQS7NRZFJWT4AUXQZ5SF2BJOME7CN5GDJ6VJX3OVJJLIF2J2JRBBDD6PYAZNLAMJIDOLJQSWTUCGDSKEBOEOFP6GARGMJJCMNGYHZPHPS47NANURZVT6EQIW2NDCE6PUFIC3YRCMDRBUDGD7GDGAG234U66W25HS6EN4OYTD7RZWUKGMF5JGH5EWW46UEJTE7YUCJJTU8GAGBXPGIVLCKAYRIAT3HMEXH7J2YMNO4WUGMNZW5DIN4MDXFTD246QHQ9GBJ7S6KJYTGYY6COIUHRAH3INJXUTUJXG4EATKH6M6OE2ZC23WVWD4ZJ10GAHFDM4MHIGKWNZERUH4GC5IMZAFN4IH7PZFJ6RAIKLZ2H356ITDSTGL11GAEXD3KCFE3CBWDGSNQ5A624AMH74B4ONAEEF2QRUWHX6SOTTAVUGKRV12GBTOTIACAKIJACTH62RZQZSZJV6QIYFVPXLSAPNCSB6Q4IYMWEKIH55D13GDZ2MUOTU45WYR4MA6IAR63OB6IU53QYGNYOAJPPJT6VBNQLSOQEZFE214GDNLRW65EWJAP2AJQO5G6F2VSNHFZJJAC3VZ2GCAO452T5ICEJMFUFPL15GD32Y4KNZI7PNFO6FKRWZO7VTCHOXMNVR3EZYLEKJ6QYN4QC3X3JUMN416GAI2EC7HSJ4DCE5QHRFYO5MYA6EV3XJCIW7D66PWUH6VUYL4DWSVGNZ217GCWGFZTDGBDQPTMU3KHRYWNDMW4PZEEHRL2INAX7UIKQB7UW7LMEH73V18GALWWEGHOMU5YODTZBVGPFP2OHCJH5VO3VKWNMW7ZNT6OECINVPQT7SQ19GCRYPAQB3TFLQE727TA3R723QIEPTP5KCMP7OMH4HVXNLCEUKPD4AZJP20GA5JVZLQAMAKQ4FVMV5XAX3EKHPIR2AHMH6FSNCWKTB664A7NMTT3NPH21GBLUQBHZGX5PM2A6FX45L3ONQVL56RNEUJ2BUSYM47A5N3Z37VPJPQ2Y22GBNPQXKGMVPBGJUT2VTKOMWNG2JAGBG7DDOH4XY6CCO55NTTV5UKL3EQ23GBLPM5I4DCKOWWVUPXKF5XONZSD22ZF3GHNDHK6ZB7PSQLIPPINXNENC24GAHHWA4EMBFHGXN42EYODCP24G7YMT7FSMBARQZNMSEIPGVQWBYCDFCY25GBTCO5WSTBEMWTLI7CXNDMFHJV7NTIPIAHTPRRNW3LC5HDNZI6M5JAQCG26GCFQGTT5JEPZDJHFT7AKA4AD5CFLH3LU6TZMSYNTNNS2JO7BKAOAEFZV27GDNKE22S6C3D3PPRGBKHB7SSQEMEZFDEZ223MOYCW73TQGRGI2BPAIG428GDBIJAOFPMGQWDUUQTJ3YFHI44MWHQHPALJQG7ZDA7D5WWEDKJYA4OHA29GAHWHBKOQRUF3NY5BLRAFPEBWMN2RAAB73F3IPSGIRRIRX6CZ3PERSCH30GACPV4RIAZ3VWN7LKZVTPLABOWBGAZUH3PVUJ5OX6PJ4TO3PNVABSR5631GCSX7FR6XYMAPHEJASF2RA3BHQV3PM4DKVW3FTSQV76IIR7GYIGJSW3W32GBTOTIACAKIJACTH62RZQZSZJV6QIYFVPXLSAPNCSB6Q4IYMWEKIH55D

📋 Smart Contract
Contract ID: CCKWQPTEXUAV7RK3WKD2T6YS4CLC4QE2KWI2MO4NHVAN4ABFJHA3YGVJ
View on Stellar Expert →
FunctionDescriptioncreate_giftCreates a new gift drop on-chaincontributeLocks XLM contribution on-chain (enforces per-user limit)get_giftFetches gift drop detailsget_contributorsReturns all contributors for a dropget_organizer_giftsReturns all drops created by organiserget_contributor_giftsReturns all drops contributed torevealReleases funds to recipient on reveal daterefundRefunds contributors if target not met

🛠️ Tech Stack
LayerTechnologyFrontendNext.js + TypeScriptBlockchainStellar TestnetSmart ContractSoroban (Rust)WalletFreighterDeploymentVercelStellar SDK@stellar/stellar-sdkData IndexingStellar Horizon APIMonitoringCustom Logger (logger.ts) + Vercel Logs

🏗️ Architecture
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

📁 Project Structure
giftdrop/
├── contracts/
│   └── gift_drop/
│       ├── Cargo.toml
│       └── src/
│           └── lib.rs              # Soroban smart contract (Rust)
├── frontend/
│   ├── app/
│   │   ├── create/                 # Create gift drop page
│   │   ├── dashboard/              # My drops and contributions
│   │   ├── drop/                   # Individual drop page
│   │   ├── reveal/                 # Reveal page
│   │   └── metrics/                # Metrics dashboard (navbar)
│   ├── lib/
│   │   ├── contract.ts             # All blockchain interactions
│   │   ├── stellar.ts              # Stellar SDK helpers
│   │   └── logger.ts               # Custom monitoring logger
│   └── components/                 # Reusable UI components
├── screenshots/
│   ├── metrics-dashboard.png
│   └── monitoring-console.png
├── SECURITY.md                     # Security checklist
├── USER_GUIDE.md                   # User guide
├── README.md
└── ARCHITECTURE.md

🚀 Installation
bash# Clone the repository
git clone https://github.com/vaiii05-hub/Stellar-Internship-Level-6.git
cd Stellar-Internship-Level-6/frontend

# Install dependencies
npm install

# Run locally
npm run dev
⚙️ Environment Setup
Create .env.local in the frontend/ folder:
envNEXT_PUBLIC_GIFT_DROP_CONTRACT=CCKWQPTEXUAV7RK3WKD2T6YS4CLC4QE2KWI2MO4NHVAN4ABFJHA3YGVJ
NEXT_PUBLIC_DEPLOYER_ADDRESS=your_deployer_address

👛 Wallet Setup for Users

Install the Freighter browser extension
Create a new wallet
Switch the network to Testnet
Get free testnet XLM from Friendbot
Visit giftdrop-five.vercel.app and connect!


🔄 User Feedback Implementations
Feedback was collected from 32 testnet users via Google Form. The following improvements were made based on their responses:
#User FeedbackImprovement Made1"My old drops were disappearing from the dashboard"Fixed expired drops — added null safety so expired drops show with an "Expired" status badge2"I had no way to verify if my contribution actually went through on blockchain"Added transaction confirmation — contributors now see a Stellar Explorer link after contributing3"I didn't know what would happen if the target amount wasn't reached"Added a clear auto-refund message on the drop detail page4"I didn't know how much was raised compared to the target"Added a progress bar showing percentage raised on each drop card5"I wanted to see my contributions separately from drops I created"Added two separate tabs — My Drops and My Contributions — on the dashboard6"I couldn't find the metrics anywhere"Added a Metrics option directly in the navbar for easy access7"Some users were contributing too much and dominating the pool"Added per-user contribution limit enforced at the smart contract level

🔮 Future Improvements
#ImprovementPlan1Mobile wallet supportIntegrate LOBSTR mobile wallet2Email notificationsNotify contributors when reveal date approaches3Multiple token supportAllow USDC contributions alongside XLM4Social sharingOne-click share drop link to WhatsApp/Telegram5Gift messagesAllow contributors to add anonymous messages

🔒 Security
View Complete Security Checklist →
Key security properties:

All funds are custodied exclusively by the smart contract — no human intermediary
Reveal and refund logic is time-locked and enforced on-chain
Contributor identities are hidden from the recipient until reveal date
Per-user contribution limits prevent griefing or fund concentration


📝 User Feedback
32 responses collected via Google Form from testnet users.
👉 View All Responses
👉 Submit New Feedback

📄 License
MIT License — feel free to use and build on this project.
