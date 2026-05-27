# 57 | Floyd's Triangle

Generate a right-angled triangle using consecutive natural numbers.

---

## 1. The Objective
Given `rows = 4`, return:
```text
1
2 3
4 5 6
7 8 9 10
```

---

## 2. Visual Logic
### The "Counter" Strategy
Keep a single variable `num = 1`.
In each row $r$, print $r$ numbers, incrementing `num` each time.

---

## 3. The "Aha!" Moment
Unlike Pascal's triangle, this has no complex math—it just tests your ability to manage **Nested Loops** and a global counter.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy: Nested Loop with Counter
 */
void printFloydTriangle(int rows) {
    int num = 1;
    for (int i = 1; i <= rows; i++) {
        for (int j = 1; j <= i; j++) {
            std::cout << num << " ";
            num++;
        }
        std::cout << std::endl;
    }
}

int main() {
    printFloydTriangle(5);
    return 0;
}
```
