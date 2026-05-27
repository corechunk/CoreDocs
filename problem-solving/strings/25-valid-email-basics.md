# 25 | Valid Email Basics

Perform a basic structural check on an email address.

---

## 1. The Objective
Determine if a string looks like a standard email (e.g., `user@domain.com`).

---

## 2. Visual Logic
### The "Critical Markers"
1. Must contain `@`.
2. Must contain `.` after the `@`.
3. `@` cannot be the first or last character.
4. No spaces.

---

## 3. The "Aha!" Moment
Don't use complex regex yet. Use `string::find()` to find the position of markers and compare their indices.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>

/**
 * Strategy: Marker Position Verification
 */
bool isBasicEmail(std::string email) {
    size_t atPos = email.find('@');
    size_t dotPos = email.find_last_of('.');
    
    if (atPos == std::string::npos || dotPos == std::string::npos) return false;
    
    // @ must not be start or end
    if (atPos == 0 || atPos == email.length() - 1) return false;
    
    // . must be after @
    if (dotPos < atPos + 2) return false;
    
    // . must not be at the end
    if (dotPos == email.length() - 1) return false;
    
    return true;
}

int main() {
    std::string e = "test@example.com";
    std::cout << "Valid format? " << (isBasicEmail(e) ? "Yes" : "No") << std::endl;
    return 0;
}
```
