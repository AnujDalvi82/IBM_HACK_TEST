# PS-006: Physics-Informed Neural Operator (PINO) for Real-Time Power Grid Cascading Failure

> **Track Domain:** Scientific Machine Learning / Power Systems / GNNs

---

## 📌 Scenario & Technical Challenge
Electrical transmission grids are vulnerable to cascading blackouts when extreme weather causes transmission line sag, short-circuits, and sudden power surges. Teams must train a machine learning model that ingests topological, thermal, and electrical metrics from a 5,000-bus power network and instantaneously predicts dynamic phase stability and line trip events.

## 🚨 Production / Industry Bottleneck
Traditional numerical simulators (Newton-Raphson power flow, Runge-Kutta 4th order integrators) scale cubically with node count. Simulating transient stability during an unfolding electrical fault takes seconds to minutes—far too slow for automated protection systems that must act within 50 to 100 milliseconds to prevent a blackout.

## 💡 Desired Solution & Technical Hints
Replace iterative numerical differential equation solvers with a Fourier Neural Operator (FNO) or Physics-Informed Graph Neural Network (PINN-GNN). Represent the power grid as an edge-attributed graph. Construct a custom physics-informed loss function that enforces Kirchhoff's Current and Voltage Laws (KCL/KVL) and thermal dissipation limits. Use spectral graph convolutions to capture long-range electrical feedback loops.

## 🛠️ Mandatory Languages
Python (PyTorch, JAX, or DeepXDE for operator training), C++ (High-speed grid topology parser and numerical baseline comparison).

## 🎯 Production Criteria
Achieve an inference latency of **< 50 milliseconds** per grid snapshot (100x faster than traditional numerical solvers), an **MSE < 0.05** against ground-truth dynamic simulations, and **< 1% physical energy conservation violation**.

---

## 📦 Dataset Package & Ingestion Policy

### Provided in `PS-006.zip`:
- `topologies/case4917_goc.m`: The full ~5,000-bus power transmission grid (**4,917 buses, 6,726 branches**) from the ARPA-E Grid Optimization Competition / PGLib.
- `topologies/case118_ieee.m`: Standard IEEE 118-bus network topology for rapid local prototyping.
- `cascades/dataset_cascades.zip`: The official **NeurIPS PowerGraph** benchmark containing pre-simulated cascading line trip sequences, outages, and Demand Not Served (DNS) labels.
- `transient_stability/GridDictionary2.csv`: The **Zenodo** transient stability simulation dataset (3,120 dynamic test cases with electrical/phase features and stability labels).
- `DATASET_INFO.md`: Complete network and cascade data manifest.

### 🌐 External Data & Ingestion Liberty:
Participants have complete liberty to ingest additional power grid benchmarks from **PGLib-OPF**, **ACTIVSg2000 (Texas synthetic grid)**, or generate synthetic fault chronics using **pandapower**, **MATPOWER**, or **Grid2Op**.

---

### How to Extract:
```bash
# Navigate to this folder and extract the dataset
unzip PS-006.zip -d dataset/
```
