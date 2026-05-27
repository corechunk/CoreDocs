# 40 | String Shuffle Check

Check if string `C` is a valid shuffle of `A` and `B`.

---

## 1. The Objective
Given `A = "abc"`, `B = "def"`, check if `C = "adbecf"` is a valid shuffle.
**Rule:** Relative order of characters from A and B must be preserved in C.

---

## 2. Visual Logic
### The "Interleave" Strategy
1. Pointer `i` for A, `j` for B, `k` for C.
2. For each char in C:
   - If `C[k] == A[i]`: Increment `i`, `k`.
   - Else if `C[k] == B[j]`: Increment `j`, `k`.
   - Else: Return `false`.

---

## 3. The "Aha!" Moment
This is like a **Merge** step in Merge Sort. You are "consuming" characters from two queues to build a third one.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>

/**
 * Strategy: Triple-Pointer Interleaving
 */
bool isValidShuffle(std::string a, std::string b, std::string c) {
    if (c.length() != a.length() + b.length()) return false;
    
    int i = 0, j = 0, k = 0;
    while (k < c.length()) {
        if (i < a.length() && c[k] == a[i]) i++;
        else if (j < b.length() && c[k] == b[j]) j++;
        else return false;
        k++;
    }
    return true;
}

int main() {
    std::cout << "Valid Shuffle? " << (isValidShuffle("abc", "def", "abdcef") ? "Yes" : "No") << std::endl;
    return 0;
}
```
