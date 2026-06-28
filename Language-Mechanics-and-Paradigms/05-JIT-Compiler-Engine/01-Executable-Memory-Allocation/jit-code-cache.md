# ⚡ JIT Code Cache Management & Instruction Flushing

## 1. JIT Code Cache Pools
JIT compilers maintain ring buffers or bump allocators over pre-allocated `PROT_EXEC` RAM blocks to store generated native machine instructions efficiently.

## 2. Instruction Cache (I-Cache) Flushing
Modern CPUs separate data caches (D-Cache) from instruction caches (I-Cache). When a JIT compiler writes dynamic machine code bytes into RAM (D-Cache), it must explicitly flush hardware caches using system builtins (e.g., `__builtin___clear_cache()`) before branching execution.
