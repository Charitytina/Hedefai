
## 📘 Project Overview: HederaDeFAI

**HederaDeFAI** is a **DeFi-inspired AI assistant** that helps users seamlessly interact with the **Hedera network** via **Telegram**. It combines the accessibility of chat interfaces with the power of decentralized finance tools — making Web3 more approachable for everyone.

### 🧩 What Problem Are We Solving?

Interacting with DeFi platforms often requires:

* Deep technical knowledge
* Manual wallet operations
* Navigation across multiple dApps

**HederaDeFAI** solves this by letting users **chat their way through Hedera actions**, including:

* Claiming test tokens
* Sending hUSDT or native Hedera tokens
* Topping up phone airtime
* Checking balances
* Viewing wallet addresses
* Unlocking **premium trading signals via Hedera micro-payments**
* (Coming soon) Swapping tokens or requesting airdrops

All of this is done through simple Telegram commands, powered by **Mastra AI** and the **Hedera Agent Kit**.

---

### 🔐 Custody Model: A Transitional Hybrid

This version of HederaDeFAI uses a **custodial model**, where user wallets are managed server-side. This:

* Makes onboarding easy for non-technical users
* Enables smooth AI execution of blockchain actions

However, it is **not fully decentralized**. In future versions, users will:

* Connect their own wallets (via WalletConnect, Hedera Wallet, or local key storage)
* Ensure full **non-custodial control**

> ⚠️ **Note:** As such, we position this tool as "DeFi-inspired" rather than a strict DeFAI implementation.

---

## 🛠️ Local Setup

### 📦 Prerequisites

* Node.js `>=18`
* `pnpm` (recommended) or `npm`
* SQLite or LibSQL file storage
* Telegram bot token from [@BotFather](https://t.me/BotFather)
* Reloadly account (for airtime)
* Hedera testnet or mainnet access
* x402 facilitator account & credentials

---

### 🔑 1. Clone the repo

```bash
git clone https://github.com/your-username/hedera-defai-bot.git
cd hedera-defai-bot
```

---

### 📁 2. Install dependencies

```bash
pnpm install
# or
npm install
```

---

### 🔐 3. Configure environment variables

Create a `.env` file:

```env
# Telegram
TELEGRAM_BOT_TOKEN=your_telegram_token

# Airtime
RELOADLY_CLIENT_ID=your_reloadly_client_id
RELOADLY_CLIENT_SECRET=your_reloadly_client_secret
RELOADLY_OPERATOR_ID=your_reloadly_operator_id

# Hedera + x402
HEDERA_NETWORK=testnet
HEDERA_OPERATOR_ID=0.0.xxxxx
HEDERA_OPERATOR_KEY=302e020100300506032b657004220420...
FACILITATOR_URL=https://your-x402-facilitator.com
PAY_TO_ADDRESS=0.0.xxxxx
USDT_TOKEN_ID=0.0.7274170

# Encryption key for wallet storage
ENCRYPTION_KEY=your_32_byte_hex_key
```

---

### 💽 4. Start the bot locally

```bash
pnpm run dev
# or
npm run dev
```

Bot will respond to messages on Telegram.

---

## 🚀 Usage Guide

### `/start`

Displays bot introduction and available commands.

---

### `/faucet`

Claim test HBAR or test hUSDT.

---

### `/claim`

Claim 1000 hUSDT from the faucet.

---

### `/balance`

Check your Hedera wallet balance (HBAR + hUSDT).

---

### `/mywallet`

Displays your wallet address for receiving tokens.

---

### `/transferusdt <receiver> <amount>`

Send hUSDT to another wallet or user. Supports wallet address or Telegram alias.

---

### `/transferhbar <receiver> <amount>`

Send HBAR to another wallet or user.

---

### `/airtime <phone> <amount> NGN`

Buy Nigerian airtime with hUSDT from your wallet (via Reloadly).

---

### `/paid-signal` *(NEW: Hedera + x402 micro-payment)*

Unlock premium trading signals:

* Requires a small Hedera payment (e.g., $0.001 hUSDT)
* Signed by the user’s Telegram wallet
* Signal delivered immediately
* Transaction traceable on HashScan

> Example:

```
/paid-signal
```

> Output Example:

```
You paid $0.001 with hUSDT on Hedera! Here's your BTC/USDT trade signal:
Buy BTC at $95,000, target $97,000, stop loss $94,000
View transaction: https://hashscan.io/testnet/transaction/0.0.xxxxx
```

---

### 💡 How It Works

* [Mastra AI Framework](https://github.com/mastra-ai/mastra) parses natural language requests.
* [Hedera Agent Kit](https://www.npmjs.com/package/@kaiachain/kaia-agent-kit) maps commands to blockchain actions.
* Executes HTS token transfers, HBAR payments, smart contract calls.
* Returns Telegram-friendly responses.

---

## 📦 Tech Stack

* **Telegram Bot API**
* **Mastra AI Framework**
* **Hedera Agent Kit** (HTS/Hedera tools)
* **x402 Express / Fetch** (Hedera micro-payments)
* **Hedera Hashgraph** (HTS, hUSDT, HBAR)
* **Reloadly API** (airtime)
* **Prisma + SQLite / LibSQLStore**
* **Node.js + TypeScript**

---

## 🛡️ Security Notice

* Wallets are encrypted and stored server-side.
* **Do not store real assets** in these wallets yet.
* Suitable for:

  * Testnet usage
  * Hackathons
  * Learning & prototyping
  * Fast DeFi + AI experiments


