# PS-010: Self-Supervised Acoustic Intent Decoding for Dysarthric Code-Switched Speech

> **Track Domain:** Speech Recognition / Representation Learning / Atypical Speech

---

## 📌 Scenario & Technical Challenge
Mainstream Automatic Speech Recognition (ASR) engines fail when processing speech from individuals with motor speech impairments (such as dysarthria or cerebral palsy), particularly when speakers switch between multiple languages mid-sentence (code-switching). Teams must engineer an acoustic representation learning pipeline that decodes underlying phonetic intent from distorted audio signals.

## 🚨 Production / Industry Bottleneck
Foundation models (like Whisper and Conformer) are trained on fluent speech and rely heavily on standard phonetic and language priors. Irregular speaking cadence, vocal tremors, and sudden cross-lingual switching cause these models to hallucinate, omit words, or lose audio-text alignment completely.

## 💡 Desired Solution & Technical Hints
Build a self-supervised representation pipeline using a dual-codebook Vector-Quantized Variational Autoencoder (VQ-VAE). Dedicate one codebook to modeling acoustic pathology features (breathiness, vocal tremors, prosodic irregularity) and a second codebook to isolate canonical phonetic content. Train a cross-attention decoder on top of the phonetic codebook using dynamic time-warping to align asynchronous acoustic streams with target multilingual text tokens.

## 🛠️ Mandatory Languages
Python (PyTorch, Torchaudio, NeMo), C++ (Low-latency acoustic feature extraction and ONNX Runtime deployment).

## 🎯 Production Criteria
Achieve at least a **20% relative reduction in Word Error Rate (WER)** on benchmark dysarthric speech datasets (such as TORGO) compared to a baseline Whisper-Large-v3 model, while maintaining a Real-Time Factor (RTF) of **< 0.3** on standard CPU architectures.

---

## 📦 Dataset Package & Ingestion Policy

### Provided in `PS-010.zip`:
- `audio/`: 16kHz mono audio recordings displaying dysarthric acoustic characteristics (vocal tremors, irregular pacing) and intra-sentential language shifts.
- `transcripts_and_phonemes.json`: Target multilingual transcripts, language transition tags, and canonical IPA phoneme target sequences for VQ-VAE codebook supervision.
- `DATASET_INFO.md`: Phoneme alignment format and WER evaluation protocols.

### 🌐 External Data & Ingestion Liberty:
Participants have complete liberty to ingest and train on the full **TORGO database** (University of Toronto / Hugging Face `abnerh/TORGO-database`), **UASpeech**, or multilingual spoken corpora from **Mozilla Common Voice**.

---

### How to Extract:
```bash
# Navigate to this folder and extract the dataset
unzip PS-010.zip -d dataset/
```
