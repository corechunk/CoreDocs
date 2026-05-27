# 21 | Anagram Check

Check if two strings are anagrams of each other.

---

## 1. The Objective
An **Anagram** is a word formed by rearranging the letters of another.
- **Example:** `"listen"` and `"silent"`. (True)
- **Example:** `"hello"` and `"bello"`. (False)

---

## 2. Visual Logic
### The "Sorting" Strategy
1. Sort both strings.
2. If `Sorted(A) == Sorted(B)`, they are anagrams.

### The "Frequency" Strategy
1. Count letters in A.
2. Subtract counts using letters in B.
3. If all counts are 0, they are anagrams.

---

## 3. The "Aha!" Moment
Two words are anagrams if and only if they have the exact same characters in the exact same quantities. Sorting is $O(n \log n)$; frequency array is $O(n)$.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>
#include <algorithm>

/**
 * Strategy: Frequency Count
 */
bool isAnagram(std::string s1, std::string s2) {
    if (s1.length() != s2.length()) return false;
    
    int freq[256] = {0};
    for (char c : s1) freq[(unsigned char)c]++;
    for (char c : s2) freq[(unsigned char)c]--;
    
    for (int i = 0; i < 256; i++) {
        if (freq[i] != 0) return false;
    }
    return true;
}

int main() {
    std::cout << "Anagram? " << (isAnagram("listen", "silent") ? "Yes" : "No") << std::endl;
    return 0;
}
```
