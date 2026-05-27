# 29 | Is Rotation (of another string)

Check if string `A` is a rotated version of string `B`.

---

## 1. The Objective
Given `"waterbottle"` and `"erbottlewat"`, return `true`.

---

## 2. Visual Logic
### The "Double String" Trick
If you concatenate `A` with itself:
`waterbottlewaterbottle`
Look! The rotation `"erbottlewat"` is hidden inside the doubled string.

---

## 3. The "Aha!" Moment
`A` is a rotation of `B` if `A.length == B.length` AND `B` is a substring of `(A + A)`. This reduces a complex rotation problem to a simple substring search.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>

/**
 * Strategy: Concatenation + Search
 */
bool isRotation(std::string s1, std::string s2) {
    if (s1.length() != s2.length() || s1.empty()) return false;
    
    std::string doubled = s1 + s1;
    return doubled.find(s2) != std::string::npos;
}

int main() {
    std::string a = "hello", b = "lohel";
    std::cout << "Is rotation? " << (isRotation(a, b) ? "Yes" : "No") << std::endl;
    return 0;
}
```
