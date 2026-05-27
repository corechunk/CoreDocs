# 🧩 Segment Tree

## 1. The Objective
A Segment Tree is a tree data structure used for storing information about intervals or segments. It allows querying which of the stored segments contain a given point, and more importantly, performing **Range Queries** (e.g., Sum, Min, Max of range $[L, R]$) in $O(\log n)$ time.

---

## 2. Visual Logic
### Storing Sums of [0, 3]
```text
          [ 0-3: Sum=10 ]
         /               \
    [ 0-1: Sum=3 ]      [ 2-3: Sum=7 ]
    /          \        /           \
[0: 1]       [1: 2]  [2: 3]        [3: 4]
```
- Every internal node represents the aggregate of its children.

---

## 3. The Logic Bridge
- **Pre-calculation:** Instead of calculating a sum every time ($O(n)$), we pre-calculate sums of segments. 
- **Logarithmic Coverage:** Any range $[L, R]$ can be represented as a union of at most $2 \log n$ nodes in the segment tree. This is why queries are so fast.
- **Dynamic Updates:** When one element changes, we only need to update the path from that leaf to the root ($O(\log n)$), keeping the tree ready for the next query.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Range Sum)

```cpp
#include <iostream>
#include <vector>

class SegmentTree {
    std::vector<int> tree;
    int n;

    void build(const std::vector<int>& arr, int node, int start, int end) {
        if (start == end) {
            tree[node] = arr[start];
            return;
        }
        int mid = (start + end) / 2;
        build(arr, 2 * node, start, mid);
        build(arr, 2 * node + 1, mid + 1, end);
        tree[node] = tree[2 * node] + tree[2 * node + 1];
    }

public:
    SegmentTree(const std::vector<int>& arr) {
        n = arr.size();
        tree.resize(4 * n);
        build(arr, 1, 0, n - 1);
    }

    int query(int node, int start, int end, int L, int R) {
        if (R < start || end < L) return 0;
        if (L <= start && end <= R) return tree[node];
        int mid = (start + end) / 2;
        return query(2 * node, start, mid, L, R) + query(2 * node + 1, mid + 1, end, L, R);
    }
};

int main() {
    std::vector<int> data = {1, 2, 3, 4};
    SegmentTree st(data);
    std::cout << "Sum of range [1, 3]: " << st.query(1, 0, 3, 1, 3) << std::endl; // 2+3+4 = 9
    return 0;
}
```

---
[➔ Back to Tree Hub](tree.md) | [➔ Back to Roadmap](../DSA-Master-Roadmap.md)
