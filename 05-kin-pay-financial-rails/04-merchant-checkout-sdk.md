# Merchant Checkout SDK

[← Previous: Virtual Debit Card Rails](03-virtual-card-infrastructure.md) | [Next: In-Terminal WASM Canvas Runtime →](../06-kinbex-game-studio/01-wasm-canvas-runtime.md)

---

## 1. Decentralized Merchant Payment Infrastructure

Kin Pay extends beyond individual trader cashouts by exposing a lightweight, embeddable **Merchant Checkout SDK**. This enables online businesses, digital creators, and regional African merchants to accept cryptocurrency payments while automatically receiving settled local fiat or stablecoins.

---

## 2. Technical Integration Flow

```mermaid
sequenceDiagram
    actor Customer as Online Shopper
    participant Store as Merchant Web App
    participant SDK as Kin Pay Checkout Modal
    participant Engine as Kin Pay Clearinghouse
    actor Merchant as Merchant Bank Account

    Customer->>Store: Click "Pay with Kin Pay"
    Store->>SDK: Initialize Payment (Amount, Currency: NGN/USD)
    SDK->>Customer: Display QR Code / Multi-Chain Wallet Connect
    Customer->>SDK: Approve Crypto Payment (USDT / $KINBEX)
    SDK->>Engine: Route & Clear Payment Instantly
    Engine-->>Store: Dispatch Webhook Event (Payment Verified)
    Engine->>Merchant: Automatically Settle Local Fiat (NGN Bank)
```

---

## 3. Merchant Benefits

* **Zero Chargeback Risk:** Cryptocurrency transactions are irreversible on-chain, eliminating the friendly-fraud chargebacks common in traditional credit card processing.
* **Instant Fiat Payouts:** Merchants do not need to hold or manage volatile cryptocurrency. Kin Pay can automatically convert payments and deposit local currency into the merchant's corporate bank account.
* **Ultra-Low Merchant Fees:** Transaction fees of $0.5\% - 1.0\%$, significantly lower than the $2.5\% - 4.5\%$ charged by traditional card processors.
* **Discounts for $KINBEX Settlements:** Merchants opting to settle or hold $KINBEX enjoy zero platform fees and promotional marketing across the Kinbex social feeds.

{% hint style="info" %}
**Developer Simplicity:**  
Merchants can integrate Kin Pay with under 10 lines of JavaScript or use pre-built plugins for Shopify, WooCommerce, and custom web applications.
{% endhint %}
