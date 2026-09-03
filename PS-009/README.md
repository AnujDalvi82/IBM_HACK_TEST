# PS-009: Reinforcement Learning & Hypergraph Neural Networks for VLSI Macro-Placement

## 📌 Scenario & Technical Challenge
In physical chip design (ASICs/SoCs), arranging hundreds of large macro blocks on a die while optimizing wirelength, timing, and heat distribution takes engineering teams weeks of manual tuning. Teams must develop a deep reinforcement learning model that automates macro-cell placement directly from an electronic netlist.

## 🚨 Production / Industry Bottleneck
Standard commercial Electronic Design Automation (EDA) tools still rely heavily on simulated annealing and analytical placers that take hours to run and scale poorly on modern multi-million gate netlists. They struggle to balance competing physical metrics, frequently producing layouts with routing congestion or localized thermal hotspots.

## 💡 Desired Solution & Technical Hints
Model the netlist as an edge-weighted hypergraph where nodes represent macro cells and hyperedges represent electrical signal nets. Use a Hypergraph Neural Network (HGNN) to generate topological node embeddings, passed to an actor-critic RL agent or diffusion policy that places macros iteratively onto a continuous 2D grid. Formulate reward functions using electrostatics-based wirelength approximations (e.g., ePlace methodology) and penalize overlapping bounding boxes with a differentiable density penalty.

## 🛠️ Mandatory Languages
Python (PyTorch Geometric, JAX), C++ (OpenROAD layout parser and fast Half-Perimeter Wirelength calculation engine).

## 🎯 Production Criteria
Must output valid, zero-overlap macro placements on unseen netlists with up to 500,000 cells in < 15 minutes, outperforming standard simulated annealing baselines in Half-Perimeter Wirelength (HPWL) by > 12%.

---

## 📦 Dataset Package
The dataset package is provided as a zip file:
- **`PS-009.zip`**

### What's Inside:
Contains `adaptec1/` from the ISPD 2005 Placement Contest (`adaptec1.nodes`, `adaptec1.nets`, `adaptec1.scl`, `adaptec1.pl`, `adaptec1.wts`).

### How to Extract:
```bash
unzip PS-009.zip -d dataset/
```
