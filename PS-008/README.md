# PS-008: Asymmetric Continual Federated Learning Under Severe Non-IID Drift & Byzantine Poisoning

## 📌 Scenario & Technical Challenge
A consortium of international banks needs to collaboratively identify evolving cross-border fraud syndicates without centralizing or sharing private financial transactions. Teams must build an asynchronous federated learning system that trains on distributed non-IID data across institutional nodes while actively defending against model poisoning and adversarial drift.

## 🚨 Production / Industry Bottleneck
Standard federated averaging (FedAvg) diverges when client data distributions are highly non-IID, causing catastrophic forgetting of historical fraud vectors when new fraud variants appear. Furthermore, distributed learning systems are highly vulnerable to sybil attacks, where compromised nodes submit poisoned gradients to degrade the global model.

## 💡 Desired Solution & Technical Hints
Implement dynamic orthogonal gradient projection: project incoming local model updates onto a subspace orthogonal to the gradient subspace of prior tasks to prevent catastrophic forgetting. Pair this with a Byzantine-resilient aggregation rule (e.g., geometric median, coordinate-wise trimmed mean, or Krum) and a differential privacy noise allocation mechanism to neutralize malicious updates.

## 🛠️ Mandatory Languages
Python (PyTorch, Flower/Syft for federated coordination), Rust (Cryptographic secure aggregation and differential privacy noise engine).

## 🎯 Production Criteria
Maintain > 90% classification accuracy on legacy fraud vectors after continuous updates, with zero model divergence under simulated scenarios where up to 30% of edge nodes submit adversarial poisoning gradients.

---

## 📦 Dataset Package
The dataset package is provided as a zip file:
- **`PS-008.zip`**

### What's Inside:
Contains `clients/client_bank_01.csv` to `client_bank_10.csv` (10 non-IID bank datasets with drift and Byzantine poisoning flags).

### How to Extract:
```bash
unzip PS-008.zip -d dataset/
```
