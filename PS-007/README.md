# PS-007: Multimodal Self-Supervised Alignment for Rare Pathologies in 3D Volumetric Scans

> **Track Domain:** 3D Medical Imaging / Foundation Models / Multimodal AI

---

## 📌 Scenario & Technical Challenge
Radiologists diagnosing rare pulmonary and neurological conditions face extreme data scarcity and a lack of detailed 3D voxel-level annotations. Teams must build a self-supervised 3D foundation model that learns spatial medical representations by directly aligning volumetric 3D CT/MRI scans with unstructured, free-text clinical radiology reports.

## 🚨 Production / Industry Bottleneck
Standard vision-language models (such as 2D CLIP) flatten scans into 2D images, discarding essential depth and volumetric relationships. Meanwhile, training supervised 3D segmentation models requires manual, slice-by-slice voxel contouring by physicians, which is prohibitively expensive and unscalable for rare diseases where only narrative clinical notes exist.

## 💡 Desired Solution & Technical Hints
Develop a 3D Masked Autoencoder (3D-MAE) paired with a cross-modal transformer. Divide the 3D volume into volumetric patches (e.g., 16x16x16 voxels) and mask 75% of them during pre-training. Align the latent features of the unmasked patches with text embeddings from clinical reports using symmetric InfoNCE contrastive loss, utilizing memory-efficient sparse 3D attention to fit within single-GPU constraints.

## 🛠️ Mandatory Languages
Python (PyTorch, MONAI, JAX), CUDA or Triton (Memory-efficient 3D sparse-attention kernels).

## 🎯 Production Criteria
Outperform standard supervised 3D baselines by at least **15% mean Average Precision (mAP)** in zero-shot rare pathology retrieval, without exceeding 24GB VRAM during forward-pass inference.

---

## 📦 Dataset Package & Ingestion Policy

### Provided in `PS-007.zip`:
- `volumes/`: 3D volumetric medical voxel arrays (.bin raw float32 format, 16x16x16) representing CT/MRI scans with localized rare pathology signatures.
- `radiology_reports.json`: Corresponding unstructured clinical free-text reports written by radiologists (e.g., lymphangioleiomyomatosis, idiopathic pulmonary fibrosis, glioblastoma multiforme).
- `DATASET_INFO.md`: Medical schema and pathology label mappings.

### 🌐 External Data & Ingestion Liberty:
Participants have complete liberty to ingest large-scale public medical datasets such as **CT-RATE (CT-CLIP)**, **LIDC-IDRI**, **MosMedData (Chest CT)**, **BraTS (Brain Tumor MRI)**, or **TotalSegmentator**.

---

### How to Extract:
```bash
# Navigate to this folder and extract the dataset
unzip PS-007.zip -d dataset/
```
