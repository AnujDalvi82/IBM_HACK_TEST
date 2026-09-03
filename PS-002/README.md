# PS-002: Autonomous eBPF-Driven L4/L7 DDoS Mitigation Engine

## 📌 Scenario & Technical Challenge
Cloud service providers face polymorphic, zero-day volumetric and application-layer DDoS attacks that bypass static firewall rules. Teams must construct an autonomous agent running across Linux user and kernel spaces that inspects raw packet rings at wire speed, detects anomalies using online statistical modeling, and dynamically compiles and injects mitigation bytecode into the kernel without interrupting established connections.

## 🚨 Production / Industry Bottleneck
Traditional user-space filtering (e.g., HAProxy, Envoy, iptables user-space rules) introduces packet copying and context-switching overhead (~microseconds per packet), saturating CPU buses and dropping legitimate traffic under 10Gbps+ volumetric attacks. Meanwhile, static rule sets cannot adapt to novel attacks that dynamically shift TCP window sizes or HTTP/2 frame patterns.

## 💡 Desired Solution & Technical Hints
Build an eXpress Data Path (XDP) driver loaded directly into the kernel network driver interface. The driver must stream telemetry into a ring buffer read by a user-space safety agent. The agent uses an online multi-armed bandit or sliding-window entropy algorithm to isolate attack vectors and dynamically updates BPF maps (such as LPM tries or hash maps) via atomic syscalls.

## 🛠️ Mandatory Languages
C / eBPF (Kernel-space packet parsing and wire-speed dropping), Rust (User-space safety agent and telemetry consumer), Python (Attack profile simulation harness).

## 🎯 Production Criteria
Must sustain wire-speed processing of 10 million packets/second (Mpps) on a simulated 10GbE interface, synthesizing and deploying kernel-level drop rules in < 500ms from attack onset.

---

## 📦 Dataset Package
The dataset package is provided as a zip file:
- **`PS-002.zip`**

### What's Inside:
Contains `attack_profiles.json` and `bpf_maps_schema.h` defining 10 Mpps attack vectors (SYN floods, UDP reflections, HTTP/2 Rapid Reset) and kernel map structures.

### How to Extract:
```bash
unzip PS-002.zip -d dataset/
```
