# 🛡️ ScamShield Agent

> AI-powered scam detection with permanent onchain reporting on X Layer

**Live Demo:** https://Tranquild1.github.io/scamshield-agent/
**Built for:** OKX Build X Hackathon 2026 | X Layer Arena
**Builder:** Damilola Ibikunle (Marskid007) | Nigeria

## 📖 Project Introduction

**Agentic Wallet:** `0xecb8bb95b8303ae1a9eeb402bb4b0e6e3d005a5b` (X Layer Mainnet)

ScamShield Agent is an AI-powered scam detection tool that helps everyday users identify fake job offers, phishing emails, crypto scams, WhatsApp messages, Telegram messages, and suspicious DMs instantly.

What makes it unique in the Web3 space: confirmed scams are reported permanently on the X Layer blockchain, building a decentralized, tamper-proof public scam database that anyone can access and verify. No central authority controls it. No report can be deleted or faked.

This directly addresses one of the biggest problems in Africa and globally: online scams that destroy lives and finances daily.

## 🏗️ Architecture Overview

```
User Input (text / screenshot)
        ↓
Groq AI (Llama 3.3 / Llama 4 Vision)
        ↓
Scam Analysis Result (score 0-100, flags, advice)
        ↓
OKX Onchain OS Market API (token/wallet lookup)
        ↓
X Layer Blockchain (onchain report via wallet tx)
        ↓
Public Dashboard (all reports visible to everyone)
```

**Tech Stack:**

| Layer | Technology |
|---|---|
| Frontend | Vanilla HTML/CSS/JS, mobile-first, no framework |
| AI | Groq API (Llama 3.3 70B for text, Llama 4 Scout for images) |
| Onchain OS | OKX Market API for token/wallet data enrichment |
| Blockchain | X Layer (EVM-compatible zkEVM L2 by OKX) |
| Wallet | OKX Wallet / MetaMask (via window.ethereum) |
| Hosting | GitHub Pages |

## ⛓️ Onchain OS Skill Usage

ScamShield Agent integrates the **OKX Onchain OS Market API** in two ways:

### 1. Token Price Lookup
When a scam message mentions a crypto token (e.g. `$W3`, `$FAKE`) or a contract address, the app automatically calls:
```
GET /api/v5/dex/market/token-price?chainIndex=196&tokenSymbol={TOKEN}
```
This shows real X Layer market data alongside the scam analysis, helping users verify whether the token actually exists and what its real price is. If the token is not found on X Layer mainnet, the app flags it as a likely fake token — a strong scam signal in itself.

### 2. Wallet Activity Check
When a scam message contains an Ethereum wallet address (`0x...`), the app calls:
```
GET /api/v5/dex/market/address-activity?chainIndex=196&address={ADDRESS}
```
This surfaces onchain activity for the flagged wallet, giving users verifiable evidence before they interact with any address.

Both calls use the **OKX Onchain OS Market module** with `chainIndex=196` (X Layer mainnet). Requests are signed with HMAC-SHA256 using the Web Crypto API directly in the browser.

## 📍 Deployment Address

ScamShield Agent is deployed on **X Layer Mainnet** (Chain ID: 196) with a dedicated Agentic Wallet as its onchain identity.

### Agentic Wallet (ScamShield Agent Identity)
```
0xecb8bb95b8303ae1a9eeb402bb4b0e6e3d005a5b
```
🔗 [View on X Layer Mainnet Explorer](https://web3.okx.com/explorer/x-layer/address/0xecb8bb95b8303ae1a9eeb402bb4b0e6e3d005a5b)

| Property | Value |
|---|---|
| Network | X Layer Mainnet |
| Chain ID | 196 |
| RPC | https://rpc.xlayer.tech |
| Explorer | https://web3.okx.com/explorer/x-layer |
| Gas token | OKB |
| Reporting mechanism | Onchain transactions with scam data encoded in calldata |

## ⚙️ Working Mechanics

### Scam Detection Flow
1. User selects message type (Job offer, Email, Crypto, WhatsApp, Telegram, X DM, Website)
2. User pastes text OR uploads a screenshot
3. AI analyzes the content and returns a scam probability score (0 to 100%), a risk level (Safe / Suspicious / Scam), specific red flags found in the message, and recommended next steps
4. OKX Onchain OS Market API enriches the result with real token price data and wallet activity from X Layer
5. User connects OKX Wallet and taps "Report as scam on X Layer"
6. A transaction is sent to X Layer blockchain with the full report encoded in calldata
7. The report appears in the public Onchain Reports dashboard, permanently and tamper-proof

### Image Analysis
When a screenshot is uploaded, the app switches to Llama 4 Scout (vision model), which reads and analyzes text directly from the image with no manual transcription needed.

## 👤 Team Members

| Name | Role | Location |
|---|---|---|
| Damilola Ibikunle (Marskid007) | Solo builder: design, frontend, AI, Web3 | Nigeria |

## 🌍 Project Positioning in X Layer Ecosystem

ScamShield Agent is **X Layer's trust layer**: a public utility built to solve the single biggest barrier to Web3 adoption in emerging markets: online scams.

Fraud is the primary reason everyday users in Africa and across the Global South distrust crypto and Web3 platforms. ScamShield Agent directly attacks this problem by giving anyone a free, instant tool to verify suspicious messages and report confirmed scams permanently on X Layer. Every scam report is a real onchain transaction, generating organic, meaningful activity on the network rather than speculative volume. Users who have never touched a blockchain wallet are onboarded naturally through the reporting flow, with OKX Wallet as their first interaction with Web3.

This positions X Layer not just as a financial chain but as infrastructure for digital safety: a narrative that resonates strongly with regulators, media, and the next wave of Web3 users entering from emerging markets. No other project in the X Layer ecosystem currently fills this role.

**Roadmap:**

| Phase | Milestone |
|---|---|
| Phase 1 (current) | Web app with AI analysis and onchain reporting |
| Phase 2 | Smart contract for a shared, queryable global scam database on X Layer |
| Phase 3 | Public API so other apps can query the scam database |
| Phase 4 | Browser extension and Telegram bot powered by X Layer |

## 🚀 How to Run Locally

1. Clone this repo
2. Open `index.html` in any browser (or serve via a local server / GitHub Pages)
3. Tap **"SETUP REQUIRED"** at the top and enter your Groq API key and OKX Onchain OS API credentials
4. Connect your OKX Wallet or MetaMask — the app will automatically switch to X Layer Mainnet (Chain ID: 196)
5. Ensure your wallet holds a small amount of OKB (mainnet) to cover gas fees for onchain reports
6. Start analyzing and reporting scams!

> **Note:** ScamShield Agent runs on X Layer Mainnet. Real OKB is required for gas fees.

## 📸 Screenshots

> Live demo: https://Tranquild1.github.io/scamshield-agent/

*Built with ❤️ for the OKX Build X Hackathon 2026*
