# AI Systems & Machine Learning Challenges — Master Benchmark Repository

Welcome to the official problem statement and dataset repository. This repository contains the complete specifications, starter datasets, and evaluation criteria for all 10 Problem Statements (PS-001 through PS-010).

---

## 🌐 Global External Data & Ingestion Policy (All Tracks)

> [!IMPORTANT]
> **Participants have complete liberty to ingest, augment, and integrate external public datasets, pre-trained models, and open-source corpora** (e.g., from Hugging Face, Kaggle, Zenodo, GitHub, or academic repositories). The provided starter datasets in each subfolder provide a validated baseline, but teams are strongly encouraged to pull in external open data to improve model robustness, generalize across domains, and achieve superior production results.

---

## 📋 Problem Statements Index

| Track ID | Problem Statement Title | Primary Domain | Mandatory Tech Stack | Starter Dataset Package |
|:---|:------------------------|:---------------|:---------------------|:------------------------|
| [**PS-001**](./PS-001/) | Zero-Copy KV-Cache Paged Allocator for Multi-Tenant LLM Serving | Systems for ML / CUDA | C++20 / Rust, Python | [`PS-001.zip`](./PS-001/PS-001.zip) |
| [**PS-002**](./PS-002/) | Autonomous eBPF-Driven L4/L7 DDoS Mitigation Engine | Kernel Networking / eBPF | C / eBPF, Rust, Python | [`PS-002.zip`](./PS-002/PS-002.zip) |
| [**PS-003**](./PS-003/) | Speculative-Decoded Sub-250ms Streaming Audio RAG Engine | Real-Time Multimedia / RAG | C++ / Rust, Go, Python | [`PS-003.zip`](./PS-003/PS-003.zip) |
| [**PS-004**](./PS-004/) | Byzantine-Resilient Multi-Agent Marketplace with SMT-Verified Guardrails | Distributed Systems / SMT | Rust, Python, Go | [`PS-004.zip`](./PS-004/PS-004.zip) |
| [**PS-005**](./PS-005/) | Dynamic Inverted-HNSW Vector Storage Engine with High-Throughput Ingestion | Database Storage Engines | Rust / C++, Go, TypeScript | [`PS-005.zip`](./PS-005/PS-005.zip) |
| [**PS-006**](./PS-006/) | Physics-Informed Neural Operator (PINO) for Real-Time Power Grid Cascading Failure | Scientific ML / Power Systems | Python, C++ | [`PS-006.zip`](./PS-006/PS-006.zip) |
| [**PS-007**](./PS-007/) | Multimodal Self-Supervised Alignment for Rare Pathologies in 3D Volumetric Scans | 3D Medical Vision / Foundation Models | Python, CUDA / Triton | [`PS-007.zip`](./PS-007/PS-007.zip) |
| [**PS-008**](./PS-008/) | Asymmetric Continual Federated Learning Under Severe Non-IID Drift & Byzantine Poisoning | Federated Learning / Security | Python, Rust | [`PS-008.zip`](./PS-008/PS-008.zip) |
| [**PS-009**](./PS-009/) | Reinforcement Learning & Hypergraph Neural Networks for VLSI Macro-Placement | ML for EDA / Physical Chip Design | Python, C++ | [`PS-009.zip`](./PS-009/PS-009.zip) |
| [**PS-010**](./PS-010/) | Self-Supervised Acoustic Intent Decoding for Dysarthric Code-Switched Speech | Speech Processing / Representation Learning | Python, C++ | [`PS-010.zip`](./PS-010/PS-010.zip) |

---

## 📂 Repository Structure

```text
competition-ps-datasets/
├── README.md                      # Master repository overview and global policy
├── PS-001/
│   ├── README.md                  # Detailed problem specification & external data hints
│   └── PS-001.zip                 # Multi-tenant variable-length stream workload trace
├── PS-002/
│   ├── README.md                  # eBPF/XDP wire-speed filtering specification
│   └── PS-002.zip                 # 10 Mpps attack vectors and BPF map schemas
├── PS-003/
│   ├── README.md                  # Sub-250ms speculative audio RAG specification
│   └── PS-003.zip                 # Flight/reactor manuals, PCM audio queries, numeric ground truth
├── PS-004/
│   ├── README.md                  # Multi-agent marketplace with formal SMT invariants
│   └── PS-004.zip                 # Order book simulation traces & adversarial jailbreaks
├── PS-005/
│   ├── README.md                  # LSM-tree vector storage engine specification
│   └── PS-005.zip                 # Dense vector benchmarks & exact brute-force top-10 kNN
├── PS-006/
│   ├── README.md                  # Power grid physics-informed neural operator specification
│   └── PS-006.zip                 # 5,000-bus topology, IEEE 118, PowerGraph cascades, Zenodo TSA
├── PS-007/
│   ├── README.md                  # 3D volumetric medical foundation model specification
│   └── PS-007.zip                 # 3D voxel scans & corresponding clinical radiology reports
├── PS-008/
│   ├── README.md                  # Continual federated learning fraud specification
│   └── PS-008.zip                 # 10 non-IID bank client datasets with Byzantine attack flags
├── PS-009/
│   ├── README.md                  # VLSI macro-placement hypergraph RL specification
│   └── PS-009.zip                 # Official ISPD 2005 industrial ASIC placement netlist (adaptec1)
└── PS-010/
    ├── README.md                  # Dysarthric code-switched speech decoding specification
    └── PS-010.zip                 # 16kHz dysarthric speech audio & phonetic alignment targets
```

---

## 🚀 Participant Instructions

1. **Clone the repository:**
   ```bash
   git clone https://github.com/AnujDalvi82/competition-ps-datasets.git
   cd competition-ps-datasets
   ```
2. **Navigate to your assigned track:**
   ```bash
   cd PS-00X
   ```
3. **Extract the dataset package:**
   ```bash
   unzip PS-00X.zip -d dataset/
   ```
4. **Review `README.md`** inside your track folder for full constraints, evaluation metrics, and recommended external data sources.
