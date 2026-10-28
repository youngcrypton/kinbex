# Sentiment NLP Co-Pilot

[← Previous: Liquidity & Volume Audit](02-liquidity-and-volume-audit.md) | [Next: African Liquidity Gateway →](../05-kin-pay-financial-rails/01-african-liquidity-gateway.md)

---

## 1. Conversational On-Chain Market Intelligence

**Kinara AI** is not merely a background security scanner; it is an interactive conversational co-pilot embedded directly into the Kinbex social and trading viewport.

Traders can prompt Kinara in plain language to analyze tokens, evaluate alpha calls, summarize market sentiment, and manage their portfolio.

---

## 2. Natural Language Social Sentiment Scoring

Kinara aggregates social streams across the Kinbex micro-blogging feed, community groups, Telegram channels, and X (Twitter) mentions to extract real-time market sentiment:

* **Organic vs. Bot Velocity:** Uses transformer-based NLP models to distinguish between authentic human discussions and coordinated bot copy-paste campaigns.
* **Sentiment Polarization Index:** Measures the ratio of bullish vs. bearish mentions, weighted by the historical credibility ($DCS$ score) of the participating accounts.
* **Trend Anomaly Alerts:** Notifies users when an overlooked token experiences a sudden organic surge in high-reputation mentions.

---

## 3. Autonomous Portfolio Intelligence

Kinara connects with the user's non-custodial wallet to deliver actionable, private insights without exposing private keys:

* **Unrealized PnL Summaries:** Real-time breakdown of gains, losses, and entry price averages across multi-chain holdings.
* **Whale Wallet Tracking:** Alerts the user if large institutional or smart-money wallets initiate accumulation or distribution in tokens held by the user.
* **Smart Rebalancing Suggestions:** Highlights portfolio concentration risks (e.g., "75% of your portfolio is currently exposed to micro-cap meme tokens on Solana; consider locking profits into stablecoins via Kin Pay").

{% hint style="info" %}
**Interactive Terminal Queries:**  
Traders can type commands directly into the terminal chat, such as:  
* `/kinara audit 0x123...` (Runs instant bytecode honeypot and liquidity scan)  
* `/kinara sentiment $TOKEN` (Summarizes 24h social momentum and bot ratio)  
* `/kinara pnl` (Generates verified PnL breakdown across all connected wallets)
{% endhint %}
