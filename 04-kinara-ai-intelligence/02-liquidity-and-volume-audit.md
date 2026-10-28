# Liquidity & Volume Audit

[← Previous: Bytecode Safety Scanner](01-bytecode-safety-scanner.md) | [Next: Sentiment NLP Co-Pilot →](03-sentiment-nlp-co-pilot.md)

---

## 1. On-Chain Liquidity & Reserve Health

A token contract may possess clean code while remaining economically dangerous due to concentrated token ownership or unlocked liquidity pools. Kinara AI provides automated telemetry on pool health and holder dispersion.

---

## 2. Reserve Locking & Burnt LP Verification

Kinara continuously monitors liquidity pool token (LP) contracts to verify whether developers can execute an abrupt "rug-pull":

* **Burnt Liquidity:** Detects whether LP tokens were permanently routed to dead addresses (e.g., `0x0000...dead`).
* **Time-Lock Escrow:** Queries decentralized lock vaults (e.g., Unicrypt, PinkSale, Team Finance) to extract lock durations, expiration timestamps, and unlock schedules.
* **Residual Developer LP:** Alerts users if the deployer retains more than $5\%$ of unlocked LP supply.

---

## 3. Holder Concentration & Cluster Analysis

Kinara scans the token distribution ledger to compute the **Gini Coefficient** of holder concentration:

$$\text{Gini} = \frac{\sum_{i=1}^n \sum_{j=1}^n |x_i - x_j|}{2n^2 \bar{x}}$$

* **Top 10 Holder Share:** Flags tokens where the top 10 non-contract wallets hold more than $20\%$ of total circulating supply.
* **Developer Connected Wallets (Cluster Detection):** Maps funding transaction graphs to identify whether multiple ostensibly independent wallets were secretly funded by the deployer's primary wallet before launch.

---

## 4. Wash-Trading & Fake Volume Filtering

Malicious developers frequently run wash-trading scripts—repeatedly swapping tokens back and forth between automated bot addresses—to inflate volume metrics and trend on platforms like DexScreener.

Kinara identifies wash-trading through:
1. **Wallet Entropy Analysis:** Tracking repeated circular swap routes with identical transaction sizes and gas parameters.
2. **Real-vs-Wash Volume Ratio:** Displaying an adjusted "True Volume" metric that discounts bot churn.

{% hint style="info" %}
**True Market Insight:**  
By separating organic trader volume from automated wash scripts, Kinbex users avoid buying into artificial liquidity traps.
{% endhint %}
