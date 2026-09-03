# PS-001: Zero-Copy KV-Cache Paged Allocator for Multi-Tenant LLM Serving

> **Track Domain:** Systems for ML / CUDA Memory Management

---

## 📌 Scenario & Technical Challenge
Commercial LLM platforms serving hundreds of concurrent user requests face severe memory fragmentation and Out-of-Memory (OOM) crashes. Because different users generate outputs of unpredictable lengths, managing GPU memory efficiently is difficult. Teams must build a custom memory manager from scratch that treats GPU VRAM like virtual memory pages, allowing non-contiguous memory allocation for Key-Value (KV) caches with shared prefix caching and zero-copy host memory offloading.

## 🚨 Production / Industry Bottleneck
Standard GPU allocators (`cudaMalloc`) require contiguous blocks of memory. To avoid mid-generation crashes, engines pre-allocate memory for the maximum possible context length (e.g., 4,096 tokens). When prompts are short or variable in length, **60% to 80% of GPU memory sits reserved but completely unused**, severely limiting how many concurrent users can fit on a single GPU.

## 💡 Desired Solution & Technical Hints
Implement an OS-style paged memory allocator. Manage fixed-size physical memory blocks (e.g., 16 tokens/block) using a centralized page table. Use a Radix Tree to share physical blocks across prompts that start with identical system instructions (prefix caching). Implement Copy-on-Write (CoW) when requests diverge, and use asynchronous CUDA streams to swap idle cache pages to pinned CPU host memory without interrupting ongoing generation.

## 🛠️ Mandatory Languages
C++20 or Rust (Core Allocator, Page Table, CUDA memory mapping), Python (Model orchestration & benchmark harness).

## 🎯 Production Criteria
Achieve significantly higher request throughput compared to naive Hugging Face baseline serving on a single 24GB VRAM GPU, maintaining zero memory leaks over a 12-hour continuous stress test running 500 variable-length concurrent streams.

---

## 📦 Dataset Package & Ingestion Policy

### Provided in `PS-001.zip`:
- `synthetic_workload_500_streams.json`: Pre-generated multi-tenant workload trace featuring 500 concurrent variable-length streams with shared system prompt tokens, individual query lengths, arrival timestamps, and generation targets.
- `DATASET_INFO.md`: Workload format documentation and verification parameters.

### 🌐 External Data & Ingestion Liberty:
Participants have complete liberty to ingest real-world prompt and conversation distributions from public datasets such as **ShareGPT**, **LMSYS Chatbot Arena**, or **UltraFeedback** to stress-test their allocator under realistic multi-turn chat dynamics.

---

### How to Extract:
```bash
# Navigate to this folder and extract the dataset
unzip PS-001.zip -d dataset/
```
