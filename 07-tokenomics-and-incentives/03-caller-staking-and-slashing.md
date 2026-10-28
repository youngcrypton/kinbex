# Caller Staking & Slashing Dynamics

[← Previous: Utility Matrix & Fee Discounts](02-utility-matrix-and-discounts.md) | [Next: Protocol DAO Governance →](04-protocol-dao-governance.md)

---

## 1. Economic Security for Signal Integrity

To prevent malicious actors from spamming signals or coordinating pump-and-dump schemes, the Verified Alpha Engine enforces **economic staking bonds**:

```
┌────────────────────────────────────────────────────────┐
│             CALLER BOND & SLASHING MODEL               │
├────────────────────────────────────────────────────────┤
│  • Entry Bond: Callers stake $KINBEX to publish        │
│  • Reputation Multiplier: Staked tokens scale DCS rank │
│  • Slashing Trigger: Proven honeypots slash bond       │
│  • Slashed Redistribution: Routed to affected users   │
└────────────────────────────────────────────────────────┘
```

---

## 2. Staking Tiers & Leaderboard Weighting

A caller's Dynamic Caller Score ($DCS$) is adjusted by their staked $KINBEX collateral:

$$\text{Effective } DCS = DCS_{\text{math}} \times \left(1 + \gamma \cdot \ln\left(1 + \frac{\text{StakedBalance}}{S_0}\right)\right)$$

Where:
* $S_0$: Baseline stake requirement (e.g., $5,000 \text{ \$KINBEX}$).
* $\gamma$: Stake scaling coefficient ($\gamma = 0.15$).

This ensures that while mathematical performance ($M_i$ and win rate) remains primary, callers with skin-in-the-game earn boosted visibility.

---

## 3. Slashing Penalties & Fraud Neutralization

If an alpha caller posts a signal that meets automated fraud criteria:
1. **Malicious Deployer Collusion:** Kinara AI detects that the caller address received pre-mint tokens from the contract deployer prior to call creation.
2. **Honeypot Activation:** The token deployer modifies transfer taxes to $99\%$ within 2 hours of the signal.

The caller's staked bond is subject to **slashing**:
* **$50\%$ Burn:** Permanently removed from circulating supply.
* **$50\%$ Insurance Pool:** Routed to a community restitution fund compensating affected followers.
* **Permanent Blacklist:** The caller's verified badge is revoked, and their historical ranking is marked with a **Malicious Actor Warning**.

{% hint style="danger" %}
**Zero Tolerance for Scams:**  
The economic staking model aligns caller incentives directly with their community's financial security.
{% endhint %}
