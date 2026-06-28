# ⚡ SIMD & Vectorization

SIMD (Single Instruction, Multiple Data) is hardware data-level parallelism. Instead of executing one math instruction per scalar data element, SIMD vector registers execute an operation on an entire array segment simultaneously.

---

### 🧠 CPU Vector Architectures

Vector performance scales with register width:

*   **Intel SSE**: 128-bit vector registers (processes $4$ floats or $2$ doubles in one cycle).
*   **Intel AVX / AVX2**: 256-bit vector registers (processes $8$ floats or $4$ doubles in one cycle).
*   **Intel AVX-512**: 512-bit vector registers (processes $16$ floats or $8$ doubles in one cycle).
*   **ARM NEON / SVE**: 128-bit (NEON) and variable width (SVE) vector engines.

---

### 💻 Compiler Auto-Vectorization & Intrinsics in C

```c
#include <immintrin.h>

// 1. Auto-vectorization Hint
// Tells compiler that pointer locations do not overlap (restrict keyword)
void add_arrays(int * restrict a, int * restrict b, int * restrict c, int n) {
    for (int i = 0; i < n; i++) {
        c[i] = a[i] + b[i]; // Loop vectorized automatically by compiler with -O3 flag
    }
}

// 2. Direct AVX2 Intrinsic Vector Add
void avx_add(float *a, float *b, float *c) {
    __m256 reg_a = _mm256_loadu_ps(a); // Load 8 floats into AVX register
    __m256 reg_b = _mm256_loadu_ps(b); // Load 8 floats into AVX register
    __m256 reg_c = _mm256_add_ps(reg_a, reg_b); // Add 8 floats in 1 instruction cycle
    _mm256_storeu_ps(c, reg_c);        // Store results back to memory
}
```
