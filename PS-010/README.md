# PS-010: Self-Supervised Acoustic Intent Decoding for Dysarthric Code-Switched Speech

## 📌 Scenario & Technical Challenge
Standard Automatic Speech Recognition (ASR) engines fail completely when processing speech from individuals with motor speech disorders (dysarthria, cerebral palsy), especially when speakers dynamically mix two or more languages mid-sentence (code-switching). Teams must engineer an acoustic representation learning pipeline that decodes underlying phonetic intent from distorted audio signals.

## 🚨 Production / Industry Bottleneck
Mainstream foundation models (e.g., Whisper, Conformer) are trained on clean, fluent speech and rely heavily on standard language-model priors. Irregular cadence, spastic phonation, vocal tremors, and sudden linguistic switching cause these models to hallucinate, skip words, or drop phonetic alignment entirely.

## 💡 Desired Solution & Technical Hints
Design a self-supervised model using a dual-codebook Vector-Quantized Variational Autoencoder (VQ-VAE). Allocate one codebook to isolate acoustic pathology characteristics (prosodic degradation, vocal tract tremors, breathiness) and a second codebook to encode canonical phonetic content. Train a dynamic time-warping cross-attention decoder on top of the phonetic codebook to align asynchronous, degraded phoneme streams with target text tokens across language shifts.

## 🛠️ Mandatory Languages
Python (PyTorch, Torchaudio, NeMo), C++ (Low-latency acoustic feature extraction and ONNX Runtime deployment).

## 🎯 Production Criteria
Achieve > 20% relative reduction in Word Error Rate (WER) on benchmark dysarthric speech datasets (e.g., TORGO) compared to baseline Whisper-Large-v3, while maintaining a Real-Time Factor (RTF) < 0.3 on standard CPU architectures.

---

## 📦 Dataset Package
The dataset package is provided as a zip file:
- **`PS-010.zip`**

### What's Inside:
Contains `audio/` (16kHz recordings with motor dysarthria characteristics) and `transcripts_and_phonemes.json` (canonical IPA phonemes and code-switch points).

### How to Extract:
```bash
unzip PS-010.zip -d dataset/
```
