# ⚡ Parallelism & Hardware Scaling

Parallelism is the **physical simultaneous execution** of multiple computational tasks on hardware to optimize throughput and processing speed.

---

### 💻 Parallelism Primitives in C

```c
// 1. SIMD Data Parallelism (4 integers processed in 1 physical instruction cycle)
typedef int v4si __attribute__ ((vector_size (16)));
v4si a = {1, 2, 3, 4};
v4si b = {5, 6, 7, 8};
v4si c = a + b; // Executed simultaneously by CPU vector hardware registers

// 2. Multi-Core Task Parallelism (Splitting workload across CPU hardware threads)
#pragma omp parallel for
for (int i = 0; i < 1000; i++) {
    process_data(i); // Loop iterations dispatched in parallel to separate CPU cores
}
```

---

### 🗺️ Redirection Directory

*   📂 [**`01-Hardware-Memory-and-Atomics/`**](./01-Hardware-Memory-and-Atomics/README.md) — CPU cache lines, MESI cache coherency, memory ordering fences, and atomic CAS primitives.
*   📂 [**`02-Advanced-Kernel-Locks/`**](./02-Advanced-Kernel-Locks/README.md) — Silicon coordination primitives (active spinlocks vs. passive sleeping futexes).
*   📂 [**`03-Parallel-Hardware-Scaling/`**](./03-Parallel-Hardware-Scaling/README.md) — Hardware vector units (AVX/NEON), Amdahl's hardware limits, and GPU massive core architectures.
