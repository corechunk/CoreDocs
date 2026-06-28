# 🚧 Memory Barriers & Reordering

Modern compilers and CPUs reorder memory operations (`reads` and `writes`) to maximize instruction pipelining and cache efficiency, provided the reordering doesn't alter single-threaded execution results. In parallel execution, this reordering breaks synchronization.

---

### 🧠 Types of Reordering

*   **Compiler Reordering**: The compiler reorders instructions during optimization passes.
*   **CPU / Hardware Reordering**: The CPU execution pipeline executes instructions out-of-order at runtime.

---

### 💻 Preventing Reordering in C

```c
// 1. Preventing Compiler Reordering (Compiler Barrier)
// Forces the compiler to flush registers to memory and re-read them
#define COMPILER_BARRIER() __asm__ __volatile__("" ::: "memory")

// 2. Preventing CPU Reordering (Hardware Memory Barrier)
// Instructs the CPU pipeline to complete all previous reads/writes before executing subsequent ones
#define CPU_MFENCE() __sync_synchronize()

// Example: Peterson's Lock state flag synchronization
flag[0] = 1;
CPU_MFENCE(); // Ensure flag write is visible to other cores before reading turn
turn = 1;
```
