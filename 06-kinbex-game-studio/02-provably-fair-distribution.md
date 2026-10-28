# Provably Fair Prize Distribution

[← Previous: In-Terminal WASM Canvas Runtime](01-wasm-canvas-runtime.md) | [Next: Tournaments & Community Sponsorships →](03-tournaments-and-sponsorships.md)

---

## 1. Non-Custodial Reward Architecture

Traditional online gaming platforms rely on centralized databases where administrators can alter game physics, withhold payouts, or manipulate odds.

Kinbex Game implements a **non-custodial, smart contract-governed reward model**:

* **Automated Prize Vaults:** Tournament buy-ins and sponsorship liquidity are locked into immutable on-chain smart contracts.
* **Instant Wallet Settlements:** Upon tournament conclusion, winnings and jackpots are routed directly into the player's non-custodial wallet without requiring manual withdrawal approval from platform administrators.
* **Zero Operator Tampering:** The platform never has custody of prize funds; smart contracts automatically release tokens according to provable leaderboard rankings.

---

## 2. Provably Fair Cryptographic Entropy

For mini-games requiring random events (e.g., item drops, obstacle generation, card shuffles), Kinbex utilizes verifiable on-chain entropy:

* **Commit-Reveal Schemes:** Players and the game engine exchange cryptographic hashes before game execution, ensuring neither party can predict or manipulate random variables.
* **Verifiable Random Function (VRF):** High-stakes tournament jackpots leverage decentralized VRF oracles to guarantee tamper-proof outcomes that can be audited publicly on-chain.

```mermaid
graph TD
    A[Tournament Registration & Entry Fee] --> B[Smart Contract Prize Pool Vault]
    B --> C[Skill-Based In-Terminal Gameplay]
    C --> D[Verifiable Score Attestation Hash]
    D --> E[On-Chain Leaderboard Finalization]
    E --> F[Smart Contract Automatically Dispatches Winnings to Wallets]

    style A fill:#0E1B38,stroke:#0047FF,stroke-width:2px,color:#fff
    style B fill:#0E1B38,stroke:#FFB800,stroke-width:2px,color:#fff
    style C fill:#0E1B38,stroke:#0047FF,stroke-width:2px,color:#fff
    style D fill:#0E1B38,stroke:#38BDF8,stroke-width:2px,color:#fff
    style E fill:#0E1B38,stroke:#FFB800,stroke-width:2px,color:#fff
    style F fill:#0E1B38,stroke:#10B981,stroke-width:2px,color:#fff
```

{% hint style="success" %}
**Transparent Jackpots:**  
Every participant can verify the total prize pool, active player count, and exact distribution percentage directly on the blockchain explorer.
{% endhint %}
