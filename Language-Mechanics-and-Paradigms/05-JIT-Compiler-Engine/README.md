# ⚡ Phase 05: JIT Compiler Engine

> ### 🛠️ Required Knowledge Depth & Requirements Coverage
> * **Virtual Memory Prototyping:** Requesting executable RAM memory pages directly from the Linux kernel using `mmap()` with `PROT_EXEC` flags, Instruction cache flushing (`clear_cache`).
> * **Profiling & Tiering Heuristics:** Invocation counters (loop/function execution tracking for hotspot detection), speculative type feedback, deoptimization safety traps.
> * **Dynamic Assembly Emission:** Writing raw machine code opcodes (x86_64/ARM) directly into RAM memory buffers, generating dynamic C-to-JIT trampolines and native branch pointers.

---

## 🗺️ Module Directory Index

- 💾 [**01-Executable-Memory-Allocation**](./01-Executable-Memory-Allocation/README.md) — Allocating executable virtual memory pages (`mmap`, `PROT_EXEC`) and managing JIT code cache pools.
- 📊 [**02-Hotspot-Profiling-Tiering**](./02-Hotspot-Profiling-Tiering/README.md) — Invocation counters for hotspot detection, speculative type feedback, and deoptimization traps.
- ⚡ [**03-Dynamic-Assembler-Emission**](./03-Dynamic-Assembler-Emission/README.md) — Emitting x86_64/ARM machine code directly into RAM buffers and generating dynamic C-to-JIT trampolines.
