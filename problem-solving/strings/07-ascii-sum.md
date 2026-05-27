# 07 | ASCII Sum

Calculate the sum of ASCII values of all characters in a string.

---

## 1. The Objective
Given `"abc"`, return `97 + 98 + 99 = 294`.

---

## 2. Visual Logic
### The Accumulator
```text
String: "Hi"
'H' -> 72
'i' -> 105
Sum: 72 + 105 = 177
```

---

## 3. The "Aha!" Moment
Characters are just small integers in disguise. You can treat `char` as an `int` directly in math operations.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>

/**
 * Strategy: Direct char-to-int accumulation
 */
long long getAsciiSum(std::string s) {
    long long sum = 0;
    for (char c : s) {
        sum += (int)c;
    }
    return sum;
}

int main() {
    std::string s = "Hello";
    std::cout << "ASCII Sum of " << s << ": " << getAsciiSum(s) << std::endl;
    return 0;
}
```
