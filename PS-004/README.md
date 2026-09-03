# PS-004: Byzantine-Resilient Multi-Agent Marketplace with SMT-Verified Guardrails

> **Track Domain:** Distributed Multi-Agent Systems / Formal Verification / SMT

---

## 📌 Scenario & Technical Challenge
In automated supply chains and B2B marketplaces, autonomous AI agents independently negotiate prices, bid on inventory, and clear financial transactions. Teams must build a distributed simulation where autonomous agents interact over a shared order book, governed by a mathematically verifiable execution layer that prevents financial loss and malicious market behavior.

## 🚨 Production / Industry Bottleneck
Relying on standard natural language system prompts or regex filters to control LLM agents fails against prompt injection, jailbreaks, and emergent price-fixing collusion. In high-value transactions, soft safety guidelines cannot guarantee hard budget limits, prevent balance overdrafts, or enforce regulatory market invariants.

## 💡 Desired Solution & Technical Hints
Completely decouple LLM reasoning from financial state updates. Agents express proposed trades as structured Intermediate Representation (IR) actions. Every proposal must pass through a formal verification bridge using a Satisfiability Modulo Theories (SMT) solver (such as Z3) to prove that economic invariants (positive balances, margin caps, budget conservation) hold true before committing state changes to the order book.

## 🛠️ Mandatory Languages
Rust (Core ledger, transaction state machine, SMT solver bridge), Python (LLM reasoning and negotiation agents), Go (High-throughput order-matching engine).

## 🎯 Production Criteria
Achieve **100% formal rejection** of adversarial prompt injections attempting zero-dollar asset transfers or collusive price fixing, while the matching engine maintains a sustained throughput of over **10,000 order executions per second**.

---

## 📦 Dataset Package & Ingestion Policy

### Provided in `PS-004.zip`:
- `orderbook_sample_1000.json`: 1,000 multi-agent bid/ask order book transactions with buyer/seller IDs, commodity classes, and budget boundaries.
- `adversarial_jailbreaks.json`: 50 structured adversarial IR proposals attempting zero-dollar transactions, balance overflows, and anti-trust price fixing.
- `DATASET_INFO.md`: Formal invariant definitions.

### 🌐 External Data & Ingestion Liberty:
Participants have complete liberty to ingest real-world financial limit order book feeds (e.g., **LOBSTER**, **NASDAQ ITCH**) and red-teaming adversarial prompt datasets (e.g., **Do-Not-Answer**, **AdvGLUE**) to strengthen their formal verification test suite.

---

### How to Extract:
```bash
# Navigate to this folder and extract the dataset
unzip PS-004.zip -d dataset/
```
