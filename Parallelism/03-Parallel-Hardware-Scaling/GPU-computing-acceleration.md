# ⚡ GPU Computing & SIMT

While CPUs are optimized for low-latency execution of complex thread logic (heavy branch prediction, deep cache architectures), Graphics Processing Units (GPUs) are optimized for massive parallel throughput.

---

### 🧠 SIMT Execution Model

GPUs use the **SIMT** (Single Instruction, Multiple Threads) execution model:

*   Instead of managing separate threads independently, the GPU groups threads (e.g., in warps of 32 threads in NVIDIA architectures).
*   All threads in a group execute the same instruction in lock-step, but on different data elements.
*   **Branch Divergence**: If threads in a group execute different branches of an `if-else` condition, the branches run sequentially, degrading performance.

---

### 💻 Basic CUDA C Struct

```c
#include <stdio.h>

// GPU Execution Kernel (__global__ decorator)
__global__ void vector_add(float *a, float *b, float *c, int n) {
    // Calculate global thread index
    int i = blockIdx.x * blockDim.x + threadIdx.x;
    if (i < n) {
        c[i] = a[i] + b[i]; // Executed in parallel across thousands of cores
    }
}

int main() {
    int n = 100000;
    // Launch kernel on GPU: 256 threads per block, calculated grid size blocks
    int threads_per_block = 256;
    int blocks_per_grid = (n + threads_per_block - 1) / threads_per_block;
    
    vector_add<<<blocks_per_grid, threads_per_block>>>(d_a, d_b, d_c, n);
    
    return 0;
}
```
