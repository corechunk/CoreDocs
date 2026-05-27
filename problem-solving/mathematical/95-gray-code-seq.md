# 95 | Gray Code Sequence

Generate all $n$-bit Gray codes.

---

## 1. The Objective
For $n=2$, return `00, 01, 11, 10`.
Each number differs by only 1 bit from the previous one.

---

## 2. Visual Logic
### The "Reflection" Strategy
1. Start with `0, 1`.
2. Reflect them: `1, 0`.
3. Add `0` to the original and `1` to the reflected:
   - `00, 01`
   - `11, 10`
Result: `0, 1, 3, 2`.

---

## 3. The "Aha!" Moment
Gray code is a "Reflected Binary Code." You can generate it recursively by reflecting the previous $n-1$ sequence and prefixing.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <string>
#include <algorithm>

/**
 * Strategy: Reflective Construction
 */
std::vector<std::string> generateGrayCode(int n) {
    if (n <= 0) return {"0"};
    if (n == 1) return {"0", "1"};
    
    std::vector<std::string> prev = generateGrayCode(n - 1);
    std::vector<std::string> res;
    
    // Add '0' to original
    for (int i = 0; i < prev.size(); i++) {
        res.push_back("0" + prev[i]);
    }
    // Add '1' to reflected (reverse order)
    for (int i = prev.size() - 1; i >= 0; i--) {
        res.push_back("1" + prev[i]);
    }
    
    return res;
}

int main() {
    std::vector<std::string> codes = generateGrayCode(3);
    for (std::string s : codes) std::cout << s << " ";
    std::cout << std::endl;
    return 0;
}
```
