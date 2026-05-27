# Complexity Analysis: The Foundation of DSA

Complexity analysis is the tool we use to compare the efficiency of different algorithms. It focuses on how the **time** and **space** requirements grow as the **input size (n)** increases.

---

## 1. Big O Notation (The "Worst Case" Limit)
Big O notation provides an upper bound on the growth rate of an algorithm. It tells us: *"In the worst possible scenario, this algorithm won't take longer than this."*

### Common Complexity Classes (Ranked from Best to Worst)

| Notation | Name | Description | Example |
| :--- | :--- | :--- | :--- |
| **O(1)** | **Constant** | Time/Space remains the same regardless of input size. | Accessing an array element by index. |
| **O(log n)** | **Logarithmic** | Execution time grows slowly as input size doubles. | Binary Search. |
| **O(n)** | **Linear** | Execution time grows in direct proportion to input size. | Simple Linear Search through an array. |
| **O(n log n)** | **Linearithmic** | Slightly worse than linear, typical for efficient sorting. | Merge Sort, Quick Sort. |
| **O(n²)** | **Quadratic** | Performance is proportional to the square of the input. | Nested loops (Bubble Sort). |
| **O(2ⁿ)** | **Exponential** | Growth doubles with every additional element. | Recursive Fibonacci. |
| **O(n!)** | **Factorial** | The absolute slowest growth; often for permutations. | Traveling Salesman Problem (Brute Force). |

---

## 2. Execution Scenarios: Best, Average, & Worst Case
Not every run of an algorithm is the same. We use different notations to describe these scenarios:

### 🟢 Best Case (Ω - Big Omega)
The minimum time/space required. This is usually the "lucky" scenario.
*   *Example:* Finding the target element at the very first index of an array (O(1)).

### 🟡 Average Case (θ - Big Theta)
The expected behavior over many runs with different inputs.
*   *Example:* Finding an element in the middle of an array (O(n/2) ≈ O(n)).

### 🔴 Worst Case (O - Big O)
The maximum time/space required. This is the **standard for comparison** because it guarantees the algorithm won't perform worse than this.
*   *Example:* The element isn't in the array at all (O(n)).

---

## 3. Amortized Analysis (The "Average" of Worst Cases)
Amortized analysis is used when an algorithm has an occasional "expensive" operation, but most of the time the operations are very "cheap."

### The "Dynamic Array" Example
1.  **Cheap Phase:** Most insertions into a Dynamic Array (like an `ArrayList` or `vector`) take **O(1)** because there is space available.
2.  **Expensive Phase:** When the array is full, it must **resize** (create a new array twice the size and copy all elements). This single operation takes **O(n)**.
3.  **Amortization:** Because the O(n) resize happens so infrequently (only after $n$ cheap O(1) operations), the *average* cost per operation over the long term is still **O(1)**.

> **Key Takeaway:** Amortized Analysis provides a more realistic view of performance for data structures that have periodic spikes in cost.

---

## Tips for Mastering Complexity
1.  **Drop the Constants:** $O(2n + 5)$ becomes $O(n)$.
2.  **Drop Non-Dominant Terms:** $O(n² + n)$ becomes $O(n²)$.
3.  **Look for Loops:** 
    *   Single loop = $O(n)$
    *   Nested loops = $O(n²)$
    *   Halving the input = $O(log n)$
