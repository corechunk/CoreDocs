# 26 | Substring Search (Manual)

Find the position of a substring within a larger string without `find()` or `strstr()`.

---

## 1. The Objective
Given `"hello world"` and `"world"`, return index `6`.

---

## 2. Visual Logic
### The "Sliding Window" Match
1. Align the small string under the big string at index `i`.
2. Check if all characters match.
3. If not, slide to index `i+1` and try again.

```text
Big:   h e l l o   w o r l d
Small: w o r l d
       ^ (mismatch at index 0)
...
Small:             w o r l d
                   ^ (all match at index 6!)
```

---

## 3. The "Aha!" Moment
The outer loop runs $N-M+1$ times. The inner loop runs $M$ times. This is the **Naive String Matching** algorithm with $O(N \times M)$ complexity.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>

/**
 * Strategy: Naive Sliding Match
 */
int findSubstring(std::string text, std::string pat) {
    int n = text.length();
    int m = pat.length();
    
    for (int i = 0; i <= n - m; i++) {
        int j;
        for (j = 0; j < m; j++) {
            if (text[i + j] != pat[j]) break;
        }
        if (j == m) return i; // Found it
    }
    return -1;
}

int main() {
    std::string t = "searching for the needle";
    std::string p = "needle";
    std::cout << "Index: " << findSubstring(t, p) << std::endl;
    return 0;
}
```
