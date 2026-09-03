# PS-006: Physics-Informed Neural Operator (PINO) for Real-Time Power Grid Cascading Failure

## 📌 Scenario & Technical Challenge
High-voltage transmission grids face cascading blackouts when extreme heat causes line sag, short-circuits, and transient power surges. Teams must train a machine learning model that takes real-time topological, thermal, and electrical metrics from a 5,000-bus power network and predicts transient phase stability and line failures instantaneously.

## 🚨 Production / Industry Bottleneck
Conventional numerical solvers (Newton-Raphson, Runge-Kutta 4th order) scale cubically with node count. Simulating transient stability during an ongoing fault takes seconds to minutes, making real-time automated intervention impossible when physical failures propagate within 50–100ms.

## 💡 Desired Solution & Technical Hints
Replace classical PDE numerical solvers with a Fourier Neural Operator (FNO) or Physics-Informed Graph Neural Network (PINN-GNN). Encode the power grid as an edge-attributed graph. Construct a composite loss function that enforces Kirchhoff's Current and Voltage Laws (KCL/KVL) and thermal dissipation equations directly. Use spectral convolutions in the frequency domain to model long-range grid feedback loops.

## 🛠️ Mandatory Languages
Python (PyTorch, JAX, or DeepXDE for operator training), C++ (High-speed grid topology parser and numerical baseline validation).

## 🎯 Production Criteria
Inference latency must be < 50ms per grid state snapshot (faster than numerical solvers) with an MSE < 0.05 compared to ground-truth simulations and < 1% physical energy conservation violation.

---

## 📦 Dataset Package
The dataset package is provided as a zip file:
- **`PS-006.zip`**

### What's Inside:
Contains `case4917_goc.m` (4,917-bus network topology), `case118_ieee.m`, `dataset_cascades.zip` (NeurIPS PowerGraph benchmark), and `GridDictionary2.csv` (Zenodo transient stability).

### How to Extract:
```bash
unzip PS-006.zip -d dataset/
```
