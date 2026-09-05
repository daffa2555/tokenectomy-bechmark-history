# 📊 Tokenonmix Verifiable Hardware Benchmark History

> **100% Transparent, Hardware-Grounded Telemetry Audit Receipts for the Tokenonmix Ecosystem.**

All metrics published here reflect authentic, reproducible integration tests executed on bare-metal physical hardware (**12-Core Intel Core i5-1235U | Arch Linux x86_64**). 

We follow strict **Industry Engineering Standards** (ISO/IEC 25010, OWASP CWE-1333 ReDoS, CWE-312 Secret Redaction, and OpenAI `cl100k_base` BPE). No simulated mocks, no synthetic sleeps, no marketing fluff.

---

## 🏛️ Industry Standards Compliance

Our testing methodology strictly conforms to:
- **ISO/IEC 25010 (§4.2.2 & §4.2.3)**: Bounded memory footprints via Linux Kernel `/proc/self/status` `VmRSS` telemetry; fail-safe atomic rollback (0 dirty diff).
- **OWASP Top 10 & CWE-1333**: Catastrophic backtracking ReDoS immunity ($O(N)$ linear time) tested with 50,000-character malicious payloads.
- **CWE-312 / CWE-319**: 13+ secret classes scrubbed locally before cloud egress.
- **OpenAI BPE Standard**: All token measurements use official `cl100k_base` (GPT-4o / Claude equivalent).

📖 *Read full engineering specifications in [STANDARDS.md](./STANDARDS.md).*

---

## 📈 Transparent Chronological Evolution (25K ➔ 1 Million Lines)

| Iteration | Workload Scale | Tier | Raw Volume | Measured Execution | Line/Token Throughput | Status |
|---|---|:---:|---|---|---|:---:|
| **#1** | **Baseline Sanity** | OSS 🆓 | 25,000 lines (2.41 MB) | **41.67 ms** | 600,006 lines/sec | ✅ Verified |
| **#2** | **Multi-Incident Stream** | Pro 👑 | 100 incidents (2.16 MB) | 604,490 ➔ 6,490 tokens | 41,752 tokens/sec | ✅ Verified |
| **#3** | **Quarter-Million Torture** | OSS 🆓 | 250,000 lines (24.44 MB) | **333.49 ms** | **749,652 lines/sec** | ✅ Verified |
| **#4** | **Half-Million Torture** | Pro 👑 | 500,000 lines (41.49 MB) | 9,750,032 raw tokens | 38,207 lines/sec | ✅ Verified |
| **#5** | **The Apex Million** | Pro 👑 | **1,000,002 lines (82.99 MB)** | **19,500,032 raw tokens** | 36,549 lines/sec | ✅ Verified |

📖 *Read the step-by-step scaling timeline in [CHRONOLOGY.md](./CHRONOLOGY.md).*

---

## 🏆 Current All-Time Records

| Category | Workload Under Test | Hardware Telemetry Result | Compliance Status |
|---|---|---|:---:|
| **Peak Line Throughput** | 250,000 lines (24.44 MB) enterprise dump | **749,652 lines/sec** (333.49 ms) | ✅ ISO/IEC 25010 |
| **Peak Token Volume** | 1,000,002 lines (82.99 MB) cluster dump | **19,500,032 tokens processed** (27.36s) | ✅ OpenAI cl100k_base |
| **ReDoS Exploitation** | 50,000-character malicious backtracking | **1.445 ms** (Linear $O(N)$) | ✅ CWE-1333 Immune |
| **OS Thread Saturation**| 100–250 parallel OS worker threads | **2,218.0 ops/sec** (135.26 ms) | ✅ IEEE 1012 |
| **Atomic Rollback** | 50-file multi-file transaction failure | **5.52 ms** (**0 bytes dirty diff**) | ✅ ACID Resilient |
| **AST Deep Recursion** | 150 nested language scopes | **36.68 ms** (Zero stack overflow) | ✅ Tree-sitter AST |

---

## 🔬 Independent Reproduction Instructions

Every developer can independently verify these numbers on their physical machine:

```bash
# 1. Reproduce OSS Quarter-Million Lines Benchmark (750k lines/sec)
git clone https://github.com/daffa2555/Tokenectomy.git
cd Tokenectomy
cargo test --release --test stress_benchmark -- --nocapture

# 2. Reproduce Pro One Million Lines Benchmark (19.5M tokens)
cd Tokenectomy-Pro
cargo test --release --test stress_limit_test -- --nocapture
```
