# PS-002: Autonomous eBPF-Driven L4/L7 DDoS Mitigation Engine

> **Track Domain:** Linux Kernel Networking / eBPF / Real-Time Defense

---

## 📌 Scenario & Technical Challenge
Modern cloud infrastructure faces fast-shifting, volumetric DDoS attacks and application-layer exploits that easily bypass static firewall rules. Teams must construct an autonomous security agent spanning Linux kernel and user space. The system must inspect packets at wire speed directly in the network driver, detect attack signatures using online statistical models, and automatically compile and apply filtering rules in real time.

## 🚨 Production / Industry Bottleneck
Traditional firewalls and user-space proxies (iptables, HAProxy, Envoy) require copying packets between the kernel and user space. Under high-volume attacks (10Gbps+), this context-switching overhead consumes all available CPU cycles, causing legitimate traffic to be dropped. Furthermore, static rules cannot adapt when attackers dynamically vary TCP window sizes or burst HTTP/2 multiplexed frames.

## 💡 Desired Solution & Technical Hints
Write an eXpress Data Path (XDP) program loaded directly into the network interface driver. Stream packet metadata to user space through an efficient BPF ring buffer. In user space, use a sliding-window entropy algorithm or an online multi-armed bandit to detect anomalies and identify malicious patterns. Then, dynamically insert drop rules into kernel BPF maps (such as Longest Prefix Match / LPM tries) via atomic system calls.

## 🛠️ Mandatory Languages
C / eBPF (Kernel-space packet parsing and wire-speed filtering), Rust (User-space safety agent and telemetry consumer), Python (Attack profile simulation harness).

## 🎯 Production Criteria
Sustain wire-speed processing of **10 million packets per second (Mpps)** on a simulated 10GbE network interface, automatically synthesizing and activating kernel-level drop rules within **500 milliseconds** of attack onset.

---

## 📦 Dataset Package & Ingestion Policy

### Provided in `PS-002.zip`:
- `attack_profiles.json`: Configuration specifications for 10 Mpps attack vectors (SYN floods with sliding window entropy, DNS UDP reflection payloads, and HTTP/2 Rapid Reset frame bursts).
- `bpf_maps_schema.h`: C header defining LPM trie keys and kernel map value schemas.
- `DATASET_INFO.md`: Attack profile schema documentation.

### 🌐 External Data & Ingestion Liberty:
Participants have complete liberty to ingest real-world network attack packet captures from open datasets such as **CIC-DDoS2019**, **CAIDA Anonymized Internet Traces**, or generate live multi-vector traffic using **TRex** or **Scapy**.

---

### How to Extract:
```bash
# Navigate to this folder and extract the dataset
unzip PS-002.zip -d dataset/
```
