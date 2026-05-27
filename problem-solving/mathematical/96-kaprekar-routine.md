# 96 | Kaprekar's Routine Visualization

Trace the steps of Kaprekar's Routine for any 4-digit number.

---

## 1. The Objective
Show every step of the subtraction process until 6174 is reached.
- **Example:** $2111 \to \dots \to 6174$.

---

## 2. Visual Logic
### The Convergence
Numbers always move towards the "center" of the 4-digit space.
```text
Step 1: 9841 - 1489 = 8352
Step 2: 8532 - 2358 = 6174
DONE
```

---

## 3. The "Aha!" Moment
Use a `while` loop that terminates when `n == 6174`. Ensure that leading zeros are handled (e.g., if the difference is 999, treat it as 0999).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
#include <iomanip>

/**
 * Strategy: Formatted Routine Simulation
 */
void visualizeKaprekar(int n) {
    if (n == 6174) {
        std::cout << "Already at 6174!" << std::endl;
        return;
    }
    
    int count = 0;
    while (n != 6174) {
        std::vector<int> d(4);
        int temp = n;
        for(int i=0; i<4; i++) { d[i] = temp % 10; temp /= 10; }
        
        std::sort(d.begin(), d.end());
        int asc = 0, desc = 0;
        for(int i=0; i<4; i++) {
            asc = asc * 10 + d[i];
            desc = desc * 10 + d[3-i];
        }
        
        n = desc - asc;
        count++;
        std::cout << "Step " << count << ": " 
                  << std::setw(4) << std::setfill('0') << desc << " - " 
                  << std::setw(4) << std::setfill('0') << asc << " = " 
                  << std::setw(4) << std::setfill('0') << n << std::endl;
        
        if (n == 0) {
            std::cout << "Routine failed (all digits identical)." << std::endl;
            break;
        }
    }
}

int main() {
    visualizeKaprekar(1234);
    return 0;
}
```
