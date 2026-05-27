# 01 | Fibonacci Sequence

Generate the Fibonacci sequence or find a specific term.

---

## 1. The Objective
The Fibonacci sequence starts with `0` and `1`. Every subsequent number is the sum of the previous two.
- **Find Nth Term:** Given `n`, return $F(n)$.
- **Print Series:** Given `n`, print all numbers from $F(0)$ to $F(n)$.

---

## 2. Visual Logic
### Tracing the "Movement" (n=5)
| Step | a (Prev) | b (Curr) | Next (a+b) | Action |
| :--- | :--- | :--- | :--- | :--- |
| Start | 0 | 1 | 1 | Print 0 |
| 1 | 1 | 1 | 2 | Print 1 |
| 2 | 1 | 2 | 3 | Print 1 |
| 3 | 2 | 3 | 5 | Print 2 |
| 4 | 3 | 5 | 8 | Print 3 |
| 5 | 5 | 8 | 13 | Print 5 |

### Recursive Tree (Finding F(4))
```text
               F(4)
              /    \
          F(3)   +  F(2)
         /   \      /   \
      F(2) + F(1) F(1) + F(0)
      /   \
   F(1) + F(0)
```

---

## 3. The "Aha!" Moment
- **Iterative:** You only need two variables to keep track of the "state" as you slide forward.
- **Recursive:** The base cases are $F(0)=0$ and $F(1)=1$. Every other call is just a combination of these two.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy A: Iterative (Printing the Series)
 * Efficiency: Time O(n), Space O(1)
 */
void printFibonacci(int n) {
    long long a = 0, b = 1;
    for (int i = 0; i <= n; i++) {
        std::cout << a << " ";
        long long next = a + b;
        a = b;
        b = next;
    }
    std::cout << std::endl;
}

/**
 * Strategy B: Recursive (Finding Nth Term)
 * Efficiency: Time O(2^n), Space O(n) - Inefficient for large n!
 */
long long findNthFib(int n) {
    if (n <= 1) return n;
    return findNthFib(n - 1) + findNthFib(n - 2);
}

int main() {
    int n = 10;
    
    std::cout << "Series up to 10 terms: ";
    printFibonacci(n);
    
    std::cout << "The 10th term (0-indexed) is: " << findNthFib(n) << std::endl;
    
    return 0;
}
```
