# PS-005: Dynamic Inverted-HNSW Vector Storage Engine with High-Throughput Write Ingestion

> **Track Domain:** Database Storage Engines / Vector Indexing / Systems

---

## 📌 Scenario & Technical Challenge
Financial intelligence and real-time analytics platforms ingest massive streams of live news, filings, and market transcripts. These documents must be embedded and immediately searchable across billions of dense vectors without service downtime. Teams must build a dedicated hybrid vector storage engine capable of ingesting high-throughput streaming writes while concurrently serving low-latency nearest-neighbor search queries.

## 🚨 Production / Industry Bottleneck
Popular vector databases (e.g., Pinecone, Milvus, Qdrant) suffer from write bottlenecks and query latency spikes during large data bursts. Updating or rebalancing Hierarchical Navigable Small World (HNSW) graph layers locks index structures, forcing engineers to trade real-time search freshness for predictable query performance.

## 💡 Desired Solution & Technical Hints
Apply a Log-Structured Merge (LSM) architecture to vector data. Write incoming vectors into an in-memory, lock-free buffer (MemTable) backed by an append-only Write-Ahead Log (WAL). When the buffer fills, flush it to disk as an immutable, quantized vector segment. Process search queries concurrently across both active memory buffers and immutable disk segments, dynamically merging top-k results.

## 🛠️ Mandatory Languages
Rust or C++ (Storage engine, LSM trees, SIMD-accelerated distance metrics), Go (gRPC query router), TypeScript (Telemetry and monitoring interface).

## 🎯 Production Criteria
Sustain a continuous write ingestion rate of **> 50,000 vectors/second** while concurrently answering **2,000 queries/second**, maintaining a P99 search latency strictly **under 15 milliseconds**.

---

## 📦 Dataset Package & Ingestion Policy

### Provided in `PS-005.zip`:
- `vectors_1k_64d.bin`: Normalized dense float32 vectors in raw binary format for write ingestion benchmarking.
- `queries_ground_truth_knn.json`: Exact top-10 brute-force nearest-neighbor ground truth for 50 query vectors.
- `DATASET_INFO.md`: Vector format and benchmarking specifications.

### 🌐 External Data & Ingestion Liberty:
Participants have complete liberty to ingest standard large-scale vector search benchmarks such as **SIFT1M / SIFT10M**, **GIST1M**, **Deep1B**, or dense text embeddings from **Cohere / OpenAI Wikipedia dumps**.

---

### How to Extract:
```bash
# Navigate to this folder and extract the dataset
unzip PS-005.zip -d dataset/
```
