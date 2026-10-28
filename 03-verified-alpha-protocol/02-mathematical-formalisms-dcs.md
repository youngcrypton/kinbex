# Mathematical Formalisms & DCS Formula

[← Previous: Signal Entry Cryptography](01-signal-entry-cryptography.md) | [Next: Anti-Sybil & Leaderboard Ranking →](03-anti-sybil-and-ranking.md)

---

## 1. Quantitative Multiplier Formula

When an alpha caller flags a token at timestamp $t_0$, the system captures initial entry price $P_0$. Over an active evaluation window $T$, continuous telemetry monitors subsequent prices $P_t$:

$$M = \frac{\max_{t \in [t_0, t_0 + T]} P_t}{P_0}$$

Where:
* $P_0$: Entry price recorded at the exact moment of signal creation.
* $P_t$: On-chain market price sampled at time $t$.
* $M$: Peak multiplier achieved (e.g., $2.5\times$, $10\times$, $100\times$).
* $T$: Maximum evaluation window (defaults to 30 days unless pool liquidity is drained).

If a token dumps and never exceeds $P_0$, the multiplier is recorded as $M \le 1.0$.

---

## 2. Dynamic Caller Score (DCS)

Ranking callers purely by their highest multiplier creates a toxic incentive: callers spam hundreds of illiquid meme tokens hoping one lucky token hits $100\times$, ignoring the 99 tokens that went to zero.

To rank callers fairly, Kinbex calculates a composite **Dynamic Caller Score ($DCS$)** that balances multiplier performance, signal frequency, historical win rate, drawdown penalties, and time decay:

$$DCS = \left[ \sum_{i=1}^{N} w_i \cdot \ln(M_i) \right] \times \text{WinRate} \times (1 - \delta \cdot \text{DrawdownRate})$$

---

## 3. Mathematical Parameter Definitions

| Symbol | Mathematical Definition | Operational Meaning |
| :---: | :--- | :--- |
| $N$ | Total Calls | Total number of verified signals published within the active evaluation cycle. |
| $M_i$ | Multiplier of Call $i$ | Peak multiplier achieved by call $i$, clamped at a baseline $1.0$ for failed calls ($M_i \ge 1.0$). |
| $w_i$ | Time-Decay Weight | Exponential decay weighting: $w_i = \exp(-\lambda \cdot (t_{\text{now}} - t_i))$, ensuring recent calls have higher significance. |
| $\lambda$ | Decay Constant | Halving parameter (set to $\lambda = 0.023$, equivalent to a 30-day half-life). |
| $\text{WinRate}$ | Successful Call Ratio | Proportion of calls achieving at least $2.0\times$ peak: $\text{WinRate} = \frac{N_{\text{win}}}{N}$ where $M_i \ge 2.0$. |
| $\text{DrawdownRate}$ | Severe Dump Ratio | Proportion of calls that suffered an $80\%$ or greater drop within 1 hour of call creation (pump-and-dump indicator). |
| $\delta$ | Risk Dampening Factor | Protocol penalty dampener set to $\delta = 0.25$, severely penalizing callers who dump on followers. |

---

## 4. Logarithmic Normalization Justification

The formula utilizes natural logarithms $\ln(M_i)$ rather than linear multipliers. This prevents single extreme outliers (e.g., an accidental $500\times$ on an un-tradable micro-pool) from completely skewing the leaderboard over callers who demonstrate consistent, repeatable $3\times$ to $10\times$ alpha with high win rates.

```
Multiplier (M)   │   Linear Impact   │   Logarithmic Impact ln(M)
─────────────────┼───────────────────┼────────────────────────────
1.0x (Break-even)│   1.0             │   0.00
2.0x (Win Target)│   2.0             │   0.69
5.0x             │   5.0             │   1.61
10.0x            │   10.0            │   2.30
50.0x            │   50.0            │   3.91
100.0x           │   100.0           │   4.61
```

{% hint style="info" %}
**Mathematical Fairness:**  
Under the $DCS$ formulation, a caller with twenty verified $5\times$ calls and an $85\%$ win rate will outrank a caller with one lucky $50\times$ call and a $10\%$ win rate.
{% endhint %}
