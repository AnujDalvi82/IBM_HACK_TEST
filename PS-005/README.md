# PS-005: Dynamic Inverted-HNSW Vector Storage Engine with High-Throughput Write Ingestion

## 📌 Scenario & Technical Challenge
Financial intelligence platforms ingest real-time tick news, filing updates, and earnings transcripts that must be immediately searchable across billions of dense vectors without downtime or query degradation. Teams must build a dedicated hybrid vector storage engine from the ground up, capable of handling extreme write workloads while serving low-latency nearest-neighbor queries.

## 🚨 Production / Industry Bottleneck
Modern vector databases (e.g., Pinecone, Milvus, Qdrant) suffer from write amplification and query latency spikes during large ingestion bursts. Rebuilding or updating HNSW graph layers locks indices, forcing engineers to trade real-time data freshness for stable search latencies.

## 💡 Desired Solution & Technical Hints
Implement a Log-Structured Merge (LSM) architecture for vector data. Ingest incoming vectors into a lock-free, in-memory buffer (MemTable) backed by an append-only Write-Ahead Log (WAL). When the buffer saturates, flush it to disk as immutable, quantized vector segments. Queries should execute a concurrent fan-out across both the active MemTable and immutable disk segments, dynamically merging k-NN results.

## 🛠️ Mandatory Languages
Rust or C++ (Storage engine, LSM trees, SIMD-accelerated distance metrics), Go (gRPC query router), TypeScript (Real-time telemetry frontend).

## 🎯 Production Criteria
Sustain a continuous write rate of > 50,000 vectors/sec while maintaining a concurrent query throughput of 2,000 queries/sec with P99 search latency strictly under 15ms.

---

## 📦 Dataset Package
The dataset package is provided as a zip file:
- **`PS-005.zip`**

### What's Inside:
Contains `vectors_1k_64d.bin` (dense float32 vectors) and `queries_ground_truth_knn.json` (exact top-10 ground-truth nearest neighbors).

### How to Extract:
```bash
unzip PS-005.zip -d dataset/
```
