# 01 | String Length

Calculate the length of a string without using built-in functions.

---

## 1. The Objective
Given a string (character array), determine how many characters it contains before the null terminator (`\0`).

---

## 2. Visual Logic
### The "Null Hunt"
In C++, C-style strings end with a hidden character `\0`.
```text
String: "Kael"
Memory: [ K | a | e | l | \0 ]
Index:    0   1   2   3    4
```
1. Start at Index 0.
2. Is it `\0`? No. (Count = 1)
3. Move to next. Is it `\0`? No. (Count = 2)
4. ...
5. Index 4 is `\0`. Stop.

---

## 3. The "Aha!" Moment
A string is just an array of bytes. You iterate until you find the "End of File" signal for that specific array, which is the byte `0`.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>

/**
 * Strategy: Pointer/Index Increment
 * Efficiency: Time O(n), Space O(1)
 */
int getStringLength(const char* str) {
    int length = 0;
    while (str[length] != '\0') {
        length++;
    }
    return length;
}

int main() {
    const char* myStr = "Hello World";
    
    std::cout << "String: " << myStr << std::endl;
    std::cout << "Manual Length: " << getStringLength(myStr) << std::endl;
    
    return 0;
}
```
