# PS-008: Asymmetric Continual Federated Learning Under Severe Non-IID Drift & Byzantine Poisoning

> **Track Domain:** Federated Learning / Continual Learning / Financial Security

---

## 📌 Scenario & Technical Challenge
A consortium of international financial institutions wants to collaboratively train an AI model to detect emerging cross-border fraud rings without sharing private customer transaction records. Teams must construct an asynchronous federated learning system that trains across decentralized banking nodes despite severe data distribution differences (non-IID data) and active adversarial attacks.

## 🚨 Production / Industry Bottleneck
Standard Federated Averaging (FedAvg) fails when client data distributions vary widely, causing global models to suffer from catastrophic forgetting of older fraud patterns when adapting to new variants. Additionally, distributed networks are vulnerable to Byzantine attacks, where malicious or compromised nodes submit poisoned gradient updates to corrupt the shared model.

## 💡 Desired Solution & Technical Hints
Implement dynamic orthogonal gradient projection: project local model updates onto a subspace orthogonal to gradients of previously learned fraud patterns to prevent catastrophic forgetting. Combine this with robust aggregation algorithms (such as geometric median, coordinate-wise trimmed mean, or Krum) and differential privacy noise allocation to identify and neutralize malicious client updates.

## 🛠️ Mandatory Languages
Python (PyTorch, Flower/Syft for federated coordination), Rust (Cryptographic secure aggregation and differential privacy engine).

## 🎯 Production Criteria
Maintain **> 90% classification accuracy** on historical fraud vectors after continuous updates, with zero model divergence when **up to 30%** of participating client nodes submit adversarial poisoning gradients.

---

## 📦 Dataset Package & Ingestion Policy

### Provided in `PS-008.zip`:
- `clients/`: 10 decentralized institutional banking node CSV datasets (`client_bank_01.csv` to `client_bank_10.csv`) with 10 PCA transaction features per record, simulating non-IID class imbalance, temporal concept drift, and adversarial Byzantine inverted labels.
- `DATASET_INFO.md`: Client partitioning specifications and attack flags.

### 🌐 External Data & Ingestion Liberty:
Participants have complete liberty to ingest and partition large-scale public financial fraud datasets such as the **Kaggle Credit Card Fraud Detection dataset**, **IEEE-CIS Fraud Detection**, or the **Elliptic Bitcoin Transaction Graph**.

---

### How to Extract:
```bash
# Navigate to this folder and extract the dataset
unzip PS-008.zip -d dataset/
```
