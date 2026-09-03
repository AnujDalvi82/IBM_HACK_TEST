# PS-004: Byzantine-Resilient Multi-Agent Marketplace with SMT-Verified Guardrails

## 📌 Scenario & Technical Challenge
In automated industrial supply chains, software agents independently negotiate bids, purchase inventory, and clear transactions across open networks. Teams must build a distributed multi-agent simulation where untrusted, self-interested agents communicate over a shared order book, governed by a deterministic, mathematically verifiable execution layer.

## 🚨 Production / Industry Bottleneck
Relying on natural language system prompts or soft regex filters for AI guardrails fails against prompt injection, jailbreaks, and emergent price-fixing collusion. When agents negotiate real transactions, soft safety measures cannot guarantee budget caps or enforce antitrust regulations.

## 💡 Desired Solution & Technical Hints
Completely separate the LLM reasoning phase from the state commit phase. Agents formulate proposals as a structured intermediate representation (IR). Every proposal must pass through a formal verification bridge using a Satisfiability Modulo Theories (SMT) solver (e.g., Z3) to verify hard economic invariants (e.g., non-negative balances, budget boundaries, margin caps) before committing state to the order book.

## 🛠️ Mandatory Languages
Rust (Core ledger, transaction state machine, SMT bridge), Python (LLM reasoning and negotiation agents), Go (High-throughput order-matching engine).

## 🎯 Production Criteria
100% formal rejection of jailbreak attempts designed to force zero-dollar transactions or under-the-table collusion, while the matching engine maintains > 10,000 matches/second throughput.

---

## 📦 Dataset Package
The dataset package is provided as a zip file:
- **`PS-004.zip`**

### What's Inside:
Contains `orderbook_sample_1000.json` (market transaction bids) and `adversarial_jailbreaks.json` (50+ exploit IR proposals).

### How to Extract:
```bash
unzip PS-004.zip -d dataset/
```
