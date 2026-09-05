# Tokenectomy OSS — Quarter-Million Lines Torture Benchmark Report

- **Date**: 2026-09-05
- **Hardware**: 12-Core Intel Core i5-1235U | Arch Linux x86_64
- **Binary**: `target/release/tokenectomy` (Compiled with release optimizations & LazyLock)

## 1. Workload Description
- Input Buffer: **250,000 lines (24.44 MB)** of realistic enterprise production logs.
- Injected Hazards: PostgreSQL database URLs with credentials, JWT access tokens, OpenAI `sk-proj` keys, AWS S3 secret keys.

## 2. Measured Telemetry
| Metric | Value |
|---|---|
| Buffer Size | 24.44 MB (250,000 lines) |
| Total Redaction Time | 333.49 ms |
| Line Throughput | **749,652 lines/sec** |
| Data Throughput | 73.3 MB/sec |
| ReDoS 50,000 Chars Exploit | **1.445 ms** (Linear $O(N)$ immune) |
| Concurrency (100 OS Threads) | **27.35 ms** (7,312.7 ops/sec) |
| Peak Memory (VmRSS) | 86.98 MB |
| Status | **PASSED (100% Sanitized, Zero Ballooning)** |
