# AI Systems & Machine Learning Challenges — Master Dataset Repository

This repository contains the complete dataset packages, benchmarks, and problem specifications for all 10 Problem Statements (PS-001 through PS-010).

Each problem statement has its own dedicated subfolder containing:
1. `README.md` with the full technical specification, mandatory tech stack, and evaluation criteria.
2. `PS-00X.zip` containing the respective dataset, traces, or benchmark workload.

---

## 📋 Problem Statements Index

| ID | Problem Statement | Domain | Mandatory Languages | Dataset Package |
|:---|:------------------|:-------|:--------------------|:----------------|
| [**PS-001**](./PS-001/) | Zero-Copy KV-Cache Paged Allocator for Multi-Tenant LLM Serving | Systems for ML / CUDA | C++20 / Rust, Python | [`PS-001.zip`](./PS-001/PS-001.zip) |
| [**PS-002**](./PS-002/) | Autonomous eBPF-Driven L4/L7 DDoS Mitigation Engine | Kernel Networking / eBPF | C / eBPF, Rust, Python | [`PS-002.zip`](./PS-002/PS-002.zip) |
| [**PS-003**](./PS-003/) | Speculative-Decoded Sub-250ms Streaming Audio RAG Engine | Real-Time Multimedia / RAG | C++ / Rust, Go, Python | [`PS-003.zip`](./PS-003/PS-003.zip) |
| [**PS-004**](./PS-004/) | Byzantine-Resilient Multi-Agent Marketplace with SMT-Verified Guardrails | Distributed Systems / Formal Methods | Rust, Python, Go | [`PS-004.zip`](./PS-004/PS-004.zip) |
| [**PS-005**](./PS-005/) | Dynamic Inverted-HNSW Vector Storage Engine with High-Throughput Ingestion | Database Storage Engines | Rust / C++, Go, TypeScript | [`PS-005.zip`](./PS-005/PS-005.zip) |
| [**PS-006**](./PS-006/) | Physics-Informed Neural Operator (PINO) for Real-Time Power Grid Cascading Failure | Scientific ML / Power Systems | Python, C++ | [`PS-006.zip`](./PS-006/PS-006.zip) |
| [**PS-007**](./PS-007/) | Multimodal Self-Supervised Alignment for Rare Pathologies in 3D Volumetric Scans | 3D Medical Vision / Foundation Models | Python, CUDA / Triton | [`PS-007.zip`](./PS-007/PS-007.zip) |
| [**PS-008**](./PS-008/) | Asymmetric Continual Federated Learning Under Severe Non-IID Drift & Byzantine Poisoning | Federated Learning / Security | Python, Rust | [`PS-008.zip`](./PS-008/PS-008.zip) |
| [**PS-009**](./PS-009/) | Reinforcement Learning & Hypergraph Neural Networks for VLSI Macro-Placement | ML for EDA / Physical Chip Design | Python, C++ | [`PS-009.zip`](./PS-009/PS-009.zip) |
| [**PS-010**](./PS-010/) | Self-Supervised Acoustic Intent Decoding for Dysarthric Code-Switched Speech | Speech Processing / Representation Learning | Python, C++ | [`PS-010.zip`](./PS-010/PS-010.zip) |

---

## 🚀 Quick Start for Participants

1. Clone this repository:
   ```bash
   git clone https://github.com/AnujDalvi82/competition-ps-datasets.git
   cd competition-ps-datasets
   ```
2. Navigate to your assigned problem statement:
   ```bash
   cd PS-00X
   unzip PS-00X.zip -d dataset/
   ```
3. Follow the instructions and evaluation criteria in `README.md`.
