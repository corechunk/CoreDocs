# 🏔️ Monotonic Stack

## 1. The Objective
A Monotonic Stack is a specialized stack that maintains its elements in a specific order (either strictly increasing or decreasing). It is used to solve "Next Greater/Smaller Element" problems in linear time.

---

## 2. Visual Logic
### Strictly Increasing Stack
When a new element `X` comes:
1. While `Stack.top() > X`, **Pop** elements.
2. **Push** `X`.
```text
Array: [ 5, 2, 10, 4 ]
1. Push 5: [5]
2. New 2: 5 > 2, Pop 5. Push 2: [2]
3. New 10: 2 < 10, Push 10: [2, 10]
4. New 4: 10 > 4, Pop 10. Push 4: [2, 4]
```

---

## 3. The Logic Bridge
- **The "Visibility" Rule:** A monotonic stack represents what elements can "see" each other without a taller/smaller element blocking the view. 
- **$O(n)$ Efficiency:** Even though there's a `while` loop inside a `for` loop, each element is pushed once and popped at most once. This makes the total complexity linear.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Next Greater Element)

```cpp
#include <iostream>
#include <vector>
#include <stack>

void nextGreater(const std::vector<int>& arr) {
    int n = arr.size();
    std::vector<int> res(n, -1);
    std::stack<int> s;

    for (int i = 0; i < n; i++) {
        while (!s.empty() && arr[s.top()] < arr[i]) {
            res[s.top()] = arr[i];
            s.pop();
        }
        s.push(i);
    }

    for (int x : res) std::cout << x << " ";
}

int main() {
    std::vector<int> data = {4, 5, 2, 25};
    std::cout << "Next Greater Elements: ";
    nextGreater(data);
    return 0;
}
```

---
[➔ Back to Stack Hub](stack.md) | [➔ Back to Roadmap](../DSA-Master-Roadmap.md)
