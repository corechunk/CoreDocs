# 18 | Last Occurrence

Find the last position of a character in a string.

---

## 1. The Objective
Given `"hello world"` and `'o'`, return index `7`.

---

## 2. Visual Logic
### The "Reverse Scan" Strategy
Start from `length - 1` and move toward `0`. The first match you find is the **Last** occurrence from the front.

```text
h e l l o   w o r l d
            <-- ^ (First match from back is 'o' at 7)
```

---

## 3. The "Aha!" Moment
Don't scan from the front and update a variable. Scanning from the back is $O(\text{distance from end})$ and much faster if the character is near the end.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>

/**
 * Strategy: Backward Linear Search
 */
int lastIndex(std::string s, char target) {
    for (int i = s.length() - 1; i >= 0; i--) {
        if (s[i] == target) return i;
    }
    return -1;
}

int main() {
    std::string s = "abracadabra";
    std::cout << "Last 'a' at: " << lastIndex(s, 'a') << std::endl;
    return 0;
}
```
