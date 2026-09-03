# PS-009: Reinforcement Learning & Hypergraph Neural Networks for VLSI Macro-Placement

> **Track Domain:** Electronic Design Automation (EDA) / RL / Hypergraphs

---

## 📌 Scenario & Technical Challenge
In modern semiconductor chip design (ASICs and SoCs), placing hundreds of large macro blocks on a silicon die while optimizing wirelength, circuit timing, and heat distribution takes engineering teams weeks of iterative manual tuning. Teams must develop a deep reinforcement learning framework that automates optimal macro placement directly from an electronic netlist.

## 🚨 Production / Industry Bottleneck
Conventional Electronic Design Automation (EDA) tools rely on analytical placers and simulated annealing algorithms that require hours to converge and scale poorly on modern multi-million gate netlists. They struggle to balance competing physical objectives, often yielding layouts with high routing congestion or severe thermal hotspots.

## 💡 Desired Solution & Technical Hints
Formulate the netlist as an edge-weighted hypergraph where nodes represent macro cells and hyperedges represent multi-pin signal nets. Use a Hypergraph Neural Network (HGNN) to generate topological node embeddings, feeding them into an actor-critic RL agent or diffusion policy that places macros iteratively on a continuous 2D plane. Use electrostatics-based wirelength approximations (such as the ePlace methodology) and apply a differentiable density penalty to prevent overlapping macros.

## 🛠️ Mandatory Languages
Python (PyTorch Geometric, JAX), C++ (OpenROAD layout parser and fast Half-Perimeter Wirelength calculation engine).

## 🎯 Production Criteria
Generate legally placed, zero-overlap macro layouts for unseen netlists with up to 500,000 cells in **under 15 minutes**, outperforming standard simulated annealing baselines in Half-Perimeter Wirelength (HPWL) by at least **12%**.

---

## 📦 Dataset Package & Ingestion Policy

### Provided in `PS-009.zip`:
- `adaptec1/`: The complete industrial ASIC placement benchmark from the **ISPD 2005 Placement Contest** (211,447 nodes, 221,142 signal nets) including `adaptec1.nodes`, `adaptec1.nets`, `adaptec1.scl`, `adaptec1.pl`, and `adaptec1.wts` in Bookshelf format.
- `DATASET_INFO.md`: Bookshelf file format specifications and legalization rules.

### 🌐 External Data & Ingestion Liberty:
Participants have complete liberty to ingest additional ASIC netlist benchmarks from the **ISPD 2005 / 2006 suites** (`adaptec2-4`, `bigblue1-4`), **MMS benchmarks**, or **CircuitNet**.

---

### How to Extract:
```bash
# Navigate to this folder and extract the dataset
unzip PS-009.zip -d dataset/
```
