# 52 | Cubic Numbers in a Range

Find all perfect cubes between $L$ and $R$.

---

## 1. The Objective
Given `L = 5` and `R = 100`, return `8, 27, 64`.
A perfect cube is $n^3$ where $n$ is an integer.

---

## 2. Visual Logic
### The "Cube Root" Strategy
1. $start = \lceil \sqrt[3]{L} \rceil$.
2. $end = \lfloor \sqrt[3]{R} \rfloor$.
3. Loop from $start$ to $end$ and print $i^3$.

---

## 3. The "Aha!" Moment
Use `pow(n, 1.0/3.0)` to calculate the cube root, but handle precision issues (e.g., `124.99999` should be treated as `125`).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <cmath>

/**
 * Strategy: Cube-root Iteration
 */
void printCubesInRange(int L, int R) {
    int start = ceil(pow(L, 1.0/3.0) - 0.000001); // Precision buffer
    int end = floor(pow(R, 1.0/3.0) + 0.000001);
    
    std::cout << "Cubes between " << L << " and " << R << ": ";
    for (int i = start; i <= end; i++) {
        long long cube = 1LL * i * i * i;
        if (cube >= L && cube <= R) {
            std::cout << cube << " ";
        }
    }
    std::cout << std::endl;
}

int main() {
    printCubesInRange(1, 1000);
    return 0;
}
```
