# PS-001: Zero-Copy KV-Cache Paged Allocator for Multi-Tenant LLM Serving

## 📌 Scenario & Technical Challenge
High-concurrency commercial SaaS platforms face extreme memory fragmentation and Out-of-Memory (OOM) aborts when running continuous batching across hundreds of fine-tuned domain-specific LoRA adapters on shared hardware. Teams must build a custom memory manager from scratch that treats physical GPU/host RAM as virtual pages, enabling non-contiguous allocation for Key-Value caches with dynamic prefix caching and zero-copy layer offloading.

## 🚨 Production / Industry Bottleneck
Modern inference engines relying on standard allocators (cudaMalloc or basic virtual memory wrappers) incur severe page thrashing and host-to-device synchronization stalls when prompt lengths vary widely. Contiguous KV-cache pre-allocation results in 60–80% memory waste per GPU, limiting multi-tenant saturation and driving server operational expenses up.

## 💡 Desired Solution & Technical Hints
Implement an OS-style paged memory allocator in a systems programming language. The core engine should manage physical blocks via a centralized page table, support copy-on-write semantics for parallel request branching, and use a Radix Tree for prefix-caching reusable system prompts. Integrate pinned host-memory swap queues using asynchronous CUDA streams to offload idle cache pages without stalling the active compute stream.

## 🛠️ Mandatory Languages
C++20 or Rust (Core Allocator, Virtual Page Table, CUDA memory mapping), Python (Model orchestration & Evaluation benchmark harness).

## 🎯 Production Criteria
Must achieve higher request throughput over naive baseline Hugging Face serving on a single 24GB VRAM target, with zero memory leaks over a 12-hour synthetic stress test running 500 concurrent variable-length streams.

---

## 📦 Dataset Package
The dataset package is provided as a zip file:
- **`PS-001.zip`**

### What's Inside:
Contains `synthetic_workload_500_streams.json` with arrival times, shared system prompt prefix tokens, and variable-length prompt/generation tokens.

### How to Extract:
```bash
unzip PS-001.zip -d dataset/
```
