# Tokenectomy Pro — One Million Lines (19.5M Tokens) Torture Benchmark Report

- **Date**: 2026-09-05
- **Hardware**: 12-Core Intel Core i5-1235U | Arch Linux x86_64
- **Binary**: `target/release/tokenectomy-pro` (Tree-sitter AST, tiktoken BPE, LazyLock)

## 1. Workload Description
- Input Buffer: **1,000,002 lines (82.99 MB)** massive cluster dump (Spark, Netty, gRPC, node_modules).
- Token Volume: **19,500,032 raw tokens** evaluated in-memory via OpenAI cl100k_base BPE.
- Critical Injection: Genuine user payment processor code buried under 500,000 framework frames.

## 2. Measured Telemetry
| Metric | Value |
|---|---|
| Buffer Size | 82.99 MB (1,000,002 lines) |
| Raw Tokens Processed | **19,500,032 tokens** |
| Post-Ectomy Clean Tokens | **10,000,053 tokens** |
| Tokens Scrubbed | 48.72% (User code 100% preserved) |
| Total Ectomy Duration | 27.36 seconds |
| Line Throughput | 36,549 lines/sec |
| ReDoS 50,000 Chars Exploit | **6.505 ms** (Linear $O(N)$ immune) |
| Concurrency (100 OS Threads) | **135.26 ms** (2,218.0 ops/sec) |
| 50-File Atomic Rollback | **5.52 ms** (0 dirty diff) |
| Deep AST Nesting (150 scopes) | **36.684 ms** (Zero stack overflow) |
| Status | **PASSED (Zero crash, zero buffer overflow)** |
