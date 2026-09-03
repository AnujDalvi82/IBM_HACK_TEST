# PS-007: Multimodal Self-Supervised Alignment for Rare Pathologies in 3D Volumetric Scans

## 📌 Scenario & Technical Challenge
Radiologists face diagnostic challenges with rare pulmonary and neurological diseases due to extreme data scarcity (class prevalence < 0.1%) and the high cost of manual voxel annotations. Teams must develop a self-supervised 3D foundation model that aligns volumetric CT/MRI scans directly with unstructured clinical radiology free-text reports.

## 🚨 Production / Industry Bottleneck
Standard 2D vision-language approaches (like CLIP) flatten depth information and lose critical volumetric spatial relationships. Existing 3D medical segmentation models require manual slice-by-slice voxel masks, which are unscalable for rare conditions where only free-text historical notes exist.

## 💡 Desired Solution & Technical Hints
Build a 3D Masked Autoencoder (3D-MAE) combined with a cross-modal transformer. Divide the 3D medical volume into 3D voxel tokens (e.g., 16x16x16 patches) and mask 75% of them during pre-training. Align the latent representations of the unmasked patches with clinical report embeddings via symmetric InfoNCE contrastive loss, incorporating flash-attention or sparse 3D convolutions to remain within single-GPU memory limits.

## 🛠️ Mandatory Languages
Python (PyTorch, MONAI, JAX), CUDA or Triton (Custom memory-efficient 3D sparse-attention kernels).

## 🎯 Production Criteria
Outperform standard fully supervised 3D baselines by > 15% mean Average Precision (mAP) in zero-shot rare pathology retrieval without exceeding 24GB VRAM during forward-pass inference.

---

## 📦 Dataset Package
The dataset package is provided as a zip file:
- **`PS-007.zip`**

### What's Inside:
Contains `volumes/` (3D voxel arrays representing rare pulmonary/neurological CT/MRI scans) and `radiology_reports.json` (unstructured clinical reports).

### How to Extract:
```bash
unzip PS-007.zip -d dataset/
```
