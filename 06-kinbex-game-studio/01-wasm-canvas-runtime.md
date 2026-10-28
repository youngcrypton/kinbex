# In-Terminal WASM Canvas Runtime

[← Previous: Merchant Checkout SDK](../05-kin-pay-financial-rails/04-merchant-checkout-sdk.md) | [Next: Provably Fair Prize Distribution →](02-provably-fair-distribution.md)

---

## 1. Gamifying the Super-Terminal Experience

**Kinbex Game** is the entertainment and interactive engagement pillar of the Kinbex ecosystem. Recognizing that crypto traders experience high cognitive stress during volatile market conditions, Kinbex embeds lightweight, competitive Web3 mini-games directly inside `kinbex.com`.

---

## 2. Technical Architecture & In-Terminal Execution

Kinbex Game is engineered for instant playability with zero barrier to entry:

```
┌────────────────────────────────────────────────────────┐
│               KINBEX GAME RUNTIME STACK                │
├────────────────────────────────────────────────────────┤
│  • Execution Engine: WebAssembly (WASM) + HTML5 Canvas │
│  • Zero-Install Architecture: Runs inside kinbex.com   │
│  • Memory Footprint: Under 15MB Initial Payload        │
│  • High Framerates: Consistent 60 FPS on Mobile Devices│
└────────────────────────────────────────────────────────┘
```

### 2.1 Zero External Installs
Users never need to visit app stores, download heavy APKs, or install browser extensions. Games launch instantaneously inside a dedicated canvas modal directly adjacent to the trading terminal.

### 2.2 Low Latency & High Frame Rates
Built with WebAssembly and hardware-accelerated WebGL/Canvas, games deliver responsive 60 FPS gameplay even on budget smartphones across emerging markets.

### 2.3 Cross-Session Synchronization
Player state, leaderboard scores, unlocked character skins, and tournament participation badges are cryptographically tied to the user's non-custodial Kinbex wallet address.

{% hint style="info" %}
**Play While You Trade:**  
Traders can play high-velocity rounds while monitoring price action and receiving Kinara AI safety alerts in the background.
{% endhint %}
