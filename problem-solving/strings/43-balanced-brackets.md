# 43 | Balanced Brackets (Multi-Type)

Check if `()`, `[]`, and `{}` are all properly nested and closed.

---

## 1. The Objective
Given `"{[()]}"`, return `true`. Given `"{[(])}"`, return `false`.

---

## 2. Visual Logic
### The "Last-In First-Out" (Stack) Strategy
1. Every time you see an **Open** bracket, push it onto a stack.
2. Every time you see a **Close** bracket:
   - Does it match the top of the stack?
   - If YES: Pop from stack.
   - If NO: Invalid.

```text
Input: {[()]}
Stack: [ { ] -> [ {, [ ] -> [ {, [, ( ]
Hit ')': Matches '(', POP.
Hit ']': Matches '[', POP.
Hit '}': Matches '{', POP.
```

---

## 3. The "Aha!" Moment
A counter isn't enough because order matters. The stack "remembers" the most recent open bracket, which **must** be the next one to close.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>
#include <stack>

/**
 * Strategy: Stack matching
 */
bool isBalanced(std::string s) {
    std::stack<char> st;
    for (char c : s) {
        if (c == '(' || c == '[' || c == '{') {
            st.push(c);
        } else {
            if (st.empty()) return false;
            char top = st.top();
            if ((c == ')' && top == '(') || 
                (c == ']' && top == '[') || 
                (c == '}' && top == '{')) {
                st.pop();
            } else {
                return false;
            }
        }
    }
    return st.empty();
}

int main() {
    std::cout << "{[()]} : " << (isBalanced("{[()]}") ? "Balanced" : "Unbalanced") << std::endl;
    std::cout << "{[(])} : " << (isBalanced("{[(])}") ? "Balanced" : "Unbalanced") << std::endl;
    return 0;
}
```
