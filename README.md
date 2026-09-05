# 📊 Tokenonmix Benchmark History & Hardware Telemetry Receipts

> **Independent, Hardware-Grounded Telemetry Audit Receipts for the Tokenonmix Autonomous MCP Infrastructure.**

All metrics in this repository represent real, reproducible integration tests executed on physical hardware (**12-Core Intel Core i5-1235U | Arch Linux x86_64**). No simulated mocks, no synthetic marketing fluff.

---

## 🏆 Current All-Time Records

| Tier | Benchmark Target | Tested Workload | Verified Hardware Outcome | Status | Report Link |
|---|---|---|---|:---:|:---:|
| **Tokenectomy OSS** | **Quarter-Million Torture** | 250,000 lines (24.44 MB) enterprise dump | **333.49 ms** (**749,652 lines/sec**). 100% secret sanitized. | ✅ Passed | [View Report](./reports/2026-09-05-oss-quarter-million.md) |
| **Tokenectomy OSS** | **ReDoS Immunity** | 50,000-character malicious backtracking payload | **1.445 ms** (Linear $O(N)$ evaluation). | ✅ Passed | [View Report](./reports/2026-09-05-oss-quarter-million.md) |
| **Tokenectomy OSS** | **OS Thread Contention** | 100 concurrent threads hammering redaction | **27.35 ms** (**7,312.7 ops/sec**). Zero race condition. | ✅ Passed | [View Report](./reports/2026-09-05-oss-quarter-million.md) |
| **Tokenectomy Pro** | **One Million Line Surgery** | 1,000,002 lines (82.99 MB / 19.5M tokens) | **19,500,032 tokens processed**. User code 100% preserved. | ✅ Passed | [View Report](./reports/2026-09-05-pro-one-million.md) |
| **Tokenectomy Pro** | **Atomic Multi-File Rollback**| 50-file transaction with intentional test failure | **5.52 ms** rollback (**0 dirty diff in Git**). | ✅ Passed | [View Report](./reports/2026-09-05-pro-one-million.md) |
| **Tokenectomy Pro** | **Deep AST Scope Traversal** | 150 nested scopes syntax healing | **36.68 ms** (Safe bounded recursion). | ✅ Passed | [View Report](./reports/2026-09-05-pro-one-million.md) |

---

## 🔬 How to Reproduce

Any developer cloning the source repositories can re-execute these exact audit benchmarks:

```bash
# 1. Tokenectomy OSS (Quarter-Million Torture)
git clone https://github.com/daffa2555/Tokenectomy.git
cd Tokenectomy
cargo test --release --test stress_benchmark -- --nocapture

# 2. Tokenectomy Pro (One Million Torture)
cd Tokenectomy-Pro
cargo test --release --test stress_limit_test -- --nocapture
```
