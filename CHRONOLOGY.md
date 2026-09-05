# ⏱️ Complete Chronological Benchmark Evolution

This log provides complete, unedited transparency into the scaling journey of the Tokenonmix engine, from baseline sanity checks to industrial-grade 1-million-line stress testing.

---

### 📍 Iteration 1: Baseline Sanity Benchmark (25,000 Lines)
- **Workload**: 25,000 lines (2.41 MB) of synthetic microservice logs.
- **Hardware Outcome**:
  - Total Redaction Time: **41.67 ms**
  - Line Throughput: **600,006 lines/sec**
  - ReDoS 50K payload: **1.37 ms**
  - Concurrency (100 Threads): **28.69 ms** (**6,970 ops/sec**)
  - Peak Memory: 24.11 MB VmRSS
- **Finding**: The engine barely warmed up; zero memory allocation overhead (`LazyLock` + `Cow`).

---

### 📍 Iteration 2: Sustained Multi-Incident Stream (604,000 Tokens)
- **Workload**: 100 consecutive microservice crash incidents (2.16 MB) + 250 parallel OS threads.
- **Hardware Outcome**:
  - Token Reduction: **604,490 ➔ 6,490 tokens (98.93% saved)**
  - Token Throughput: **41,752 tokens/sec**
  - 250 Threads Saturation: **865 ms** (**867 ops/sec**)
  - Peak Memory: 83.77 MB VmRSS
- **Finding**: Ectomy filters out 98%+ of framework bloat while preserving user code byte-for-byte across Java, Python, Go, and Rust.

---

### 📍 Iteration 3: Quarter-Million Lines Stress Torture (250,000 Lines)
- **Workload**: 250,000 lines (24.44 MB) of enterprise production logs.
- **Hardware Outcome**:
  - Total Redaction Time: **333.49 ms**
  - Line Throughput: **749,652 lines/sec**
  - Data Throughput: **73.3 MB/sec**
  - ReDoS 50K payload: **1.445 ms**
  - Concurrency (100 Threads): **27.35 ms** (**7,312.7 ops/sec**)
  - Peak Memory: 86.98 MB VmRSS
- **Finding**: Throughput scaled to nearly 750,000 lines per second on single-node consumer laptop hardware.

---

### 📍 Iteration 4: Half-Million Lines Stress Torture (500,000 Lines)
- **Workload**: 500,000 lines (41.49 MB) containing **9,750,032 raw tokens** (tiktoken BPE).
- **Hardware Outcome**:
  - Total Ectomy Duration: **13.09 seconds**
  - Line Throughput: **38,207 lines/sec**
  - Token Reduction: **9,750,032 ➔ 5,000,053 tokens (48.72% scrubbed)**
  - 50-File Atomic Rollback: **5.20 ms**
  - Deep AST Nesting (150 scopes): **26.038 ms**
- **Finding**: Passed 100% without memory leak or buffer overflow.

---

### 📍 Iteration 5: The Apex Benchmark — ONE MILLION LINES (1,000,000 Lines / 19.5M Tokens)
- **Workload**: 1,000,002 lines (82.99 MB) containing **19,500,032 raw tokens** (tiktoken BPE).
- **Hardware Outcome**:
  - Total Ectomy Duration: **27.36 seconds**
  - Line Throughput: **36,549 lines/sec**
  - Data Throughput: **3.0 MB/sec**
  - Raw Tokens Evaluated: **19,500,032 tokens**
  - Cleaned Tokens: **10,000,053 tokens** (User code 100% preserved)
  - ReDoS 50K payload: **6.505 ms** (Linear $O(N)$)
  - Concurrency (100 Threads): **135.26 ms** (**2,218.0 multithreaded ops/sec**)
  - 50-File Atomic Rollback: **5.52 ms**
  - Deep AST Nesting (150 scopes): **36.684 ms**
- **Finding**: Bounded memory, zero crashes, and zero dirty diffs across 1 million lines.
