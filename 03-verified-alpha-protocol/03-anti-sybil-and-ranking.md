# Anti-Sybil & Leaderboard Ranking

[← Previous: Mathematical Formalisms & DCS Formula](02-mathematical-formalisms-dcs.md) | [Next: Bytecode Safety Scanner →](../04-kinara-ai-intelligence/01-bytecode-safety-scanner.md)

---

## 1. Threat Vectors in Decentralized Alpha Ranking

Public leaderboards inherently attract adversarial gaming. Without robust protections, malicious actors attempt three primary attacks:

1. **Volume/Spam Attacks:** Creating automated bots that call thousands of newly created tokens every minute to manufacture statistical flukes.
2. **Wash-Volume Collusion:** Self-buying illiquid tokens to artificially pump multipliers before dumping on terminal users.
3. **Sybil Identity Cloning:** Creating multiple burner wallets to test calls, discarding losers and publicizing only the winning burner account.

---

## 2. Multi-Layer Anti-Sybil Defenses

Kinbex implements a four-pillar defense architecture to neutralize ranking manipulation:

### 2.1 Staked Economic Bond ($KINBEX Requirement)
To publish verified signals that impact the global public leaderboard, callers must stake a baseline tier of $KINBEX tokens. 
* Burner bot accounts with zero stake cannot register verified signals.
* Malicious callers engaging in proven rug-pull coordination are subject to **governance slashing** of their staked bond.

### 2.2 Liquidity Depth Floor
A token signal is only admitted into the $DCS$ calculation if the target pool satisfies a minimum decentralized liquidity threshold:
$$\text{Liquidity}_{\text{Pool}} \ge \$5,000 \text{ USD Equivalent}$$
Calls on tokens with negligible liquidity (e.g., $100 pools where small buys create artificial $100\times$ spikes) are flagged as **Unverified Micro-Caps** and quarantined from the official leaderboard.

### 2.3 Severe Drawdown Penalties ($\delta \cdot \text{DrawdownRate}$)
If a token experiences a price decline exceeding $80\%$ within 60 minutes of signal creation, the call is indexed as a **Catastrophic Drawdown**. The $DCS$ algorithm applies a steep penalty multiplier, rapidly degrading the caller's rank.

---

## 3. Tiered Leaderboard Badge System

Callers who maintain high $DCS$ scores across extended evaluation periods earn cryptographic profile badges rendered across the terminal:

| Badge Tier | Minimum $DCS$ | Required Win Rate | Evaluation Period | Caller Privileges |
| :---: | :---: | :---: | :---: | :--- |
| **Bronze Caller** | $15.0$ | $\ge 40\%$ | 14 Days | Standard Feed Visibility |
| **Silver Caller** | $45.0$ | $\ge 55\%$ | 30 Days | Feed Boost & Verified Checkmark |
| **Gold Alpha** | $100.0$ | $\ge 65\%$ | 60 Days | Monetized Gated Group Rights |
| **Diamond Master**| $250.0$ | $\ge 75\%$ | 90 Days | Featured Terminal Banner & Staking Multipliers |

{% hint style="success" %}
**Community Trust:**  
Traders can immediately verify whether an influencer is genuinely profitable or riding temporary hype by clicking their profile to review their complete, audited call history.
{% endhint %}
