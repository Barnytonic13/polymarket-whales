<div align="center">

# 🐋 polymarket-whales

**Watch where smart money moves on Polymarket — in real time.**

[Quick Start](#-quick-start) · [Configuration](#️-configuration) · [Features](#-features) · [Contributing](#-contributing)

![demo](https://raw.githubusercontent.com/al1enjesus/polymarket-whales/main/assets/demo.png)

</div>

---

## What is this?

`polymarket-whales` monitors the Polymarket CLOB API and fires an alert — in your terminal and via Telegram — the moment a trade above your threshold hits the books. No sign-up, no API key, no infrastructure. Just Python.

---

## 📋 Example Output

**Terminal:**

```
══════════════════════════════════════════════════
🐋  polymarket-whales
══════════════════════════════════════════════════
  Min trade size : $500
  Check interval : 30s
  Telegram alerts: ON
══════════════════════════════════════════════════

🐋 WHALE ALERT  2026-03-20 14:23:01
───────────────────────────────────────────
Market : Will Trump tweet about crypto today?
Side   : YES
Amount : $2,847.00
Price  : 0.7300  (73% YES)
───────────────────────────────────────────

🐋 WHALE ALERT  2026-03-20 14:26:44
───────────────────────────────────────────
Market : Fed rate cut in March 2026?
Side   : NO
Amount : $12,500.00
Price  : 0.3100  (69% NO)
───────────────────────────────────────────
```

**Telegram:**

```
🐋 WHALE ALERT  2026-03-20 14:23:01
──────────────────────────────
Market : Will Trump tweet about crypto today?
Side   : ✅ YES
Amount : $2,847.00
Price  : 0.7300  (73% YES)
──────────────────────────────
```

---

## ⚡ Quick Start

```bash
git clone https://github.com/al1enjesus/polymarket-whales
cd polymarket-whales
pip install -r requirements.txt
python main.py
```

Works out of the box. Terminal output is live immediately. Add Telegram credentials for push alerts.

---

## ⚙️ Configuration

**.env**

```env
TELEGRAM_BOT_TOKEN=123456789:ABCDEFabcdef...
TELEGRAM_CHAT_ID=-1001234567890
MIN_TRADE_SIZE=500
```

**config.yaml**

```yaml
min_trade_size: 500    # USD — alerts fire above this
check_interval: 30     # seconds between polls

telegram:
  bot_token: ""
  chat_id: ""

polymarket:
  api_url: "https://clob.polymarket.com"
```

Environment variables take priority over `config.yaml`.

**Getting Telegram credentials:**

1. Message [@BotFather](https://t.me/BotFather) → `/newbot` → copy the token
2. Message [@userinfobot](https://t.me/userinfobot) → copy your chat ID
3. For a channel: add the bot as admin and use the channel's chat ID (starts with `-100`)

---

## ✨ Features

- ✅ Real-time polling of the Polymarket CLOB API
- ✅ Configurable minimum trade size (USD)
- ✅ Colorized terminal output — YES in green, NO in red
- ✅ Telegram push alerts to any chat, group, or channel
- ✅ Auto-resolves market names from condition IDs
- ✅ Trade deduplication — no double alerts
- ✅ Graceful handling of network errors and API timeouts
- ✅ No database, no Docker, no setup beyond `pip install`

---

## 🛠️ Advanced

**Background service:**

```bash
nohup python main.py > whales.log 2>&1 &
```

**Custom config path:**

```bash
python main.py /path/to/my-config.yaml
```

**Running 24/7 on a VPS:** Any $5/month VPS works fine — the script uses <10MB RAM.

---

## 🤝 Contributing

PRs and issues welcome. Good first contributions:

- [ ] Discord webhook support
- [ ] Filter alerts by specific market or category
- [ ] Track wallet addresses across trades
- [ ] Configurable alert cooldown per market
- [ ] Historical whale activity export (CSV/JSON)

---

## 📡 Live Whale Feed

Don't want to self-host? Follow [@polymarketwhales_ai](https://t.me/polymarketwhales_ai) on Telegram for a live feed of whale trades — no setup required.

---

## 🤖 Want trades executed automatically?

This tool watches. [PolyClawster](https://polyclawster.com?ref=gh-whales) acts.  
AI agent that copies whale moves and trades Polymarket 24/7 — no VPN, no KYC, start with $10.

[![PolyClawster](https://img.shields.io/badge/PolyClawster-Trade%20Automatically-8b5cf6?style=for-the-badge)](https://polyclawster.com?ref=gh-whales)

---

MIT · Built by [Virixlabs](https://github.com/virixlabs)
