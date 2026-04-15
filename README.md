# 🛡️ ScamShield Agent

> AI-powered scam detection with permanent onchain reporting on X Layer

**Live Demo:** https://Tranquild1.github.io/scamshield-agent/
**Built for:** OKX Build X Hackathon 2026 — X Layer Arena
**Builder:** Damilola Ibikunle (Marskid007) — Nigeria

---

## 📖 Project Introduction

**Agentic Wallet:** `0xecb8bb95b8303ae1a9eeb402bb4b0e6e3d005a5b` (X Layer Testnet)

ScamShield Agent is an AI-powered scam detection tool that helps everyday users identify fake job offers, phishing emails, crypto scams, WhatsApp messages, Telegram messages, and suspicious DMs — instantly.

What makes it unique in the Web3 space: **confirmed scams are reported permanently on the X Layer blockchain**, building a decentralized, tamper-proof public scam database that anyone can access and verify. No central authority controls it. No report can be deleted or faked.

This directly addresses one of the biggest problems in Africa and globally — online scams that destroy lives and finances daily.

---

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
- Frontend: Vanilla HTML/CSS/JS (no framework — mobile-first)
- AI: Groq API (Llama 3.3 70B for text, Llama 4 Scout for images)
- Onchain OS: OKX Market API for token/wallet data enrichment
- Blockchain: X Layer (EVM-compatible zkEVM L2 by OKX)
- Wallet: OKX Wallet / MetaMask (via window.ethereum)
- Hosting: GitHub Pages

---

## ⛓️ Onchain OS Skill Usage

ScamShield Agent integrates the **OKX Onchain OS Market API** in two ways:

### 1. Token Price Lookup
When a scam message mentions a crypto token (e.g. `$W3`, `$FAKE`) or contract address, the app automatically calls:
```
GET /api/v5/dex/market/token-price?chainIndex=196&tokenSymbol={TOKEN}
```
This shows real X Layer market data alongside the scam analysis — helping users verify if the token actually exists and what its real price is.

### 2. Wallet Activity Check
When a scam message contains an Ethereum wallet address (`0x...`), the app calls:
```
GET /api/v5/dex/market/address-activity?chainIndex=196&address={ADDRESS}
```
This shows onchain activity for the wallet — a powerful signal for detecting scam wallets.

Both calls use the **OKX Onchain OS Market module** with `chainIndex=196` (X Layer mainnet).

---

## 📍 Deployment Address

ScamShield Agent is deployed on **X Layer Mainnet** (Chain ID: 196) with a dedicated Agentic Wallet as its onchain identity.

### Agentic Wallet (ScamShield Agent Identity)
```
0xecb8bb95b8303ae1a9eeb402bb4b0e6e3d005a5b
```
🔗 [View on X Layer Mainnet Explorer](https://web3.okx.com/explorer/x-layer/address/0xecb8bb95b8303ae1a9eeb402bb4b0e6e3d005a5b)

- **Network:** X Layer Mainnet
- **Chain ID:** 196
- **RPC:** https://rpc.xlayer.tech
- **Explorer:** https://web3.okx.com/explorer/x-layer
- **Gas token:** OKB
- **Reporting mechanism:** Onchain transactions with scam data encoded in calldata

---

## ⚙️ Working Mechanics

### Scam Detection Flow
1. User selects message type (Job offer, Email, Crypto, WhatsApp, Telegram, X DM, Website)
2. User pastes text OR uploads a screenshot
3. AI analyzes the content and returns:
   - **Scam probability score** (0–100%)
   - **Risk level:** Safe / Suspicious / Scam
   - **Red flags** found in the message
   - **What to do** next
4. OKX Onchain OS Market API enriches the result with real token/wallet data
5. User connects OKX wallet and taps "Report as scam on X Layer"
6. Transaction is sent to X Layer blockchain with report encoded in calldata
7. Report appears in the public **Onchain Reports** dashboard

### Image Analysis
When a screenshot is uploaded, the app switches to Llama 4 Scout (vision model) which reads and analyzes text directly from the image — no manual transcription needed.

---

## 👤 Team Members

| Name | Role | Location |
|---|---|---|
| Damilola Ibikunle (Marskid007) | Solo builder — design, frontend, AI, Web3 | Nigeria |

---

## 🌍 Project Positioning in X Layer Ecosystem

ScamShield Agent positions itself as **X Layer's trust layer** — a public utility that makes the X Layer ecosystem safer for new users entering Web3.

**Why this matters for X Layer:**
- Scams are the #1 barrier to Web3 adoption in Africa and emerging markets
- A decentralized scam database on X Layer creates real utility and daily active transactions
- Every scam report is an onchain transaction — driving organic activity on X Layer
- The app introduces non-crypto-native users to OKX Wallet and X Layer naturally
- Directly leverages OKX Onchain OS Market API — showcasing its real-world value

**Growth path:**
- Phase 1: Web app with onchain reporting (current)
- Phase 2: Smart contract for shared global scam database
- Phase 3: API for other apps to query the scam database
- Phase 4: Browser extension + Telegram bot powered by X Layer

---

## 🚀 How to Run Locally

1. Clone this repo
2. Open `index.html` in any browser (or serve via a local server / GitHub Pages)
3. Tap **"SETUP REQUIRED"** at the top and enter your Groq API key and OKX Onchain OS API credentials
4. Connect your OKX Wallet or MetaMask — the app will automatically switch to **X Layer Mainnet** (Chain ID: 196)
5. Ensure your wallet holds a small amount of **OKB** (mainnet) to cover gas fees for onchain reports
6. Start analyzing and reporting scams!

> **Note:** ScamShield Agent runs on **X Layer Mainnet** — real OKB is required for gas, not testnet tokens.

---

## 📸 Screenshots

> Live demo: https://Tranquild1.github.io/scamshield-agent/

---

*Built with ❤️ for the OKX Build X Hackathon 2026*
