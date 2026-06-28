# 📐 Algorithmic Scaling Laws

Two mathematical models govern the maximum performance gains achievable by executing workloads in parallel across multiple CPU cores.

---

### 🧠 Amdahl's Law (Fixed Workload)

Amdahl's law calculates the speedup limit for a program when the **total workload size is fixed**. It shows that the speedup is limited by the sequential fraction of the program that cannot be parallelized.

$$S_{\text{latency}}(s) = \frac{1}{(1 - p) + \frac{p}{s}}$$

Where:
*   $S_{\text{latency}}$ is the theoretical speedup.
*   $p$ is the parallel fraction of the code ($0 \le p \le 1$).
*   $s$ is the speedup factor / number of parallel cores.
*   As $s \to \infty$, speedup limit $\to \frac{1}{1-p}$ (if $5\%$ of code is sequential, max speedup is $20\times$ regardless of core counts).

---

### 🧠 Gustafson's Law (Scaled Workload)

Gustafson's law calculates speedup limits when the **workload size scales** dynamically as core count increases (typical of modern scientific workloads).

$$S_{\text{latency}}(s) = s + (1 - s)(1 - p)$$

Gustafson's Law shows that sequential code does not limit speedup as severely if the problem size scales, allowing near-linear scaling for large-scale data computations.
