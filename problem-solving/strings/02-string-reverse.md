# 02 | String Reverse (In-place)

Reverse a string without using extra memory for a new string.

---

## 1. The Objective
Given `"Gemini"`, transform it to `"inimGe"` in the same memory space.

---

## 2. Visual Logic
### The "Two-Pointer" Swap
1. Put one pointer at the **Start** and one at the **End**.
2. Swap the characters.
3. Move pointers toward the middle.
4. Stop when they meet.

```text
[ G | e | m | i | n | i ]
  S               E      (Swap G and i)
    S           E        (Swap e and n)
      S       E          (Swap m and i)
```

---

## 3. The "Aha!" Moment
You don't need a second string. Since swapping `A` and `B` only requires one temporary character variable, you can flip the entire string "in-place" in $O(n/2)$ steps.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>
#include <algorithm> // for std::swap

/**
 * Strategy: Two-Pointer Swap
 * Efficiency: Time O(n), Space O(1)
 */
void reverseInPlace(std::string &s) {
    int start = 0;
    int end = s.length() - 1;
    
    while (start < end) {
        // Swap values at pointers
        std::swap(s[start], s[end]);
        
        // Move pointers
        start++;
        end--;
    }
}

int main() {
    std::string text = "Netchunk";
    std::cout << "Original: " << text << std::endl;
    
    reverseInPlace(text);
    std::cout << "Reversed: " << text << std::endl;
    
    return 0;
}
```
