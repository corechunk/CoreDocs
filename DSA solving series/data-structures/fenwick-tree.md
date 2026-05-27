# 📉 Fenwick Tree (Binary Indexed Tree)

## 1. The Objective
The Fenwick Tree (or BIT) is a data structure that can efficiently update elements and calculate prefix sums of a table of values. It is a more **Space-Efficient** alternative to the Segment Tree for prefix-based operations.

---

## 2. Visual Logic
### The Power of 2
Fenwick Tree uses the binary representation of indices to store partial sums.
```text
Idx 1 (0001): Stores [1]
Idx 2 (0010): Stores [1-2]
Idx 3 (0011): Stores [3]
Idx 4 (0100): Stores [1-4]
```
- Each index `i` is responsible for a range of length `LSB(i)` (Least Significant Bit).

---

## 3. The Logic Bridge
- **BIT Manipulation:** We move through the tree using the trick `i += (i & -i)` to update and `i -= (i & -i)` to query. This allows traversing the "logical" tree in $O(\log n)$ using only bitwise math.
- **Space Win:** Unlike a Segment Tree which needs $4N$ space, a Fenwick Tree only needs $N+1$ space (it's an array, not a tree of objects).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Prefix Sum)

```cpp
#include <iostream>
#include <vector>

class FenwickTree {
    std::vector<int> bit;
    int n;

public:
    FenwickTree(int n) : n(n) { bit.assign(n + 1, 0); }

    void update(int i, int delta) {
        for (; i <= n; i += i & -i) bit[i] += delta;
    }

    int query(int i) {
        int sum = 0;
        for (; i > 0; i -= i & -i) sum += bit[i];
        return sum;
    }
};

int main() {
    FenwickTree ft(5);
    ft.update(1, 10);
    ft.update(3, 20);
    
    std::cout << "Sum up to index 3: " << ft.query(3) << std::endl; // 10 + 20 = 30
    return 0;
}
```

---
[➔ Back to Tree Hub](tree.md) | [➔ Back to Roadmap](../DSA-Master-Roadmap.md)
