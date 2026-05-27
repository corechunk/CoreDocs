# ⚖️ Stable vs. Unstable Algorithms

## 1. The Objective
An algorithm is **Stable** if it preserves the relative order of elements with equal keys. In C++, this is a critical distinction when sorting complex data (like sorting users by Last Name, then by First Name).

---

## 2. Visual Logic
### The Stability Test
Data: `[3a, 2, 3b, 1]` (where 3a and 3b have the same value)
- **Stable Sort:** `[1, 2, 3a, 3b]` (3a stays before 3b)
- **Unstable Sort:** `[1, 2, 3b, 3a]` (Relative order flipped!)

---

## 3. The Logic Bridge
- **Why it matters:** If you sort a spreadsheet by "Date" and then by "Category", a stable sort ensures that within each category, items are still sorted by date. An unstable sort would scramble the dates.
- **STL Choice:** 
    - `std::sort` is **Unstable** (usually faster).
    - `std::stable_sort` is **Stable** (uses extra memory if needed).
    - `std::partition` is **Unstable**; `std::stable_partition` is **Stable**.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Stable Sort)

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

struct Student {
    std::string name;
    int grade;
};

int main() {
    std::vector<Student> students = {{"Alice", 90}, {"Bob", 80}, {"Charlie", 90}};

    // Sort by grade only
    std::stable_sort(students.begin(), students.end(), [](auto a, auto b) {
        return a.grade > b.grade;
    });

    // Alice (90) is guaranteed to stay before Charlie (90)
    for (auto s : students) std::cout << s.name << " ";
    
    return 0;
}
```

---
[➔ Back to Algorithm Hub](04-algorithms.md)
