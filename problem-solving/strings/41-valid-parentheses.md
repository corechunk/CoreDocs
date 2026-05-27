# 41 | Valid Parentheses

Check if a string has balanced opening and closing parentheses `()`.

---

## 1. The Objective
Given `"(())"`, return `true`. Given `"())( "`, return `false`.

---

## 2. Visual Logic
### The "Balance Counter"
1. Start with `balance = 0`.
2. For every `(`: `balance++`.
3. For every `)`: `balance--`.
4. **Rule:** Balance must never drop below 0 (cannot close before opening).
5. **Final Rule:** Balance must be exactly 0 at the end.

---

## 3. The "Aha!" Moment
Simple counting works for a single type of bracket. If you have multiple types (`[]`, `{}`), you need a **Stack** (Problem 43).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>

/**
 * Strategy: Counter-based Balance
 */
bool isValidParentheses(std::string s) {
    int balance = 0;
    for (char c : s) {
        if (c == '(') balance++;
        else if (c == ')') balance--;
        
        if (balance < 0) return false; // Found ) before (
    }
    return balance == 0;
}

int main() {
    std::cout << "Valid? (()) : " << (isValidParentheses("(())") ? "Yes" : "No") << std::endl;
    std::cout << "Valid? ())( : " << (isValidParentheses("())( ") ? "Yes" : "No") << std::endl;
    return 0;
}
```
