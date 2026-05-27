# 24 | Valid IP Basics

Check if a string is a valid IPv4 address.

---

## 1. The Objective
Given `"192.168.1.1"`, return `true`. Given `"256.0.0.1"`, return `false`.

---

## 2. Visual Logic
### The "Octet" Rules
An IPv4 address has:
1. Exactly 4 parts (octets).
2. Separated by `.` dots.
3. Each part is a number from 0 to 255.
4. No leading zeros (e.g., "01" is invalid).

---

## 3. The "Aha!" Moment
Split the string by `.` and validate each part. This tests your **Parsing** skills.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>
#include <vector>
#include <sstream>

/**
 * Strategy: Split and Range-check
 */
bool isValidIP(std::string ip) {
    std::stringstream ss(ip);
    std::string part;
    int count = 0;
    
    while (std::getline(ss, part, '.')) {
        count++;
        if (part.empty() || part.length() > 3) return false;
        
        // Check for leading zero
        if (part.length() > 1 && part[0] == '0') return false;
        
        // Check for non-digits
        for (char c : part) if (!isdigit(c)) return false;
        
        int val = std::stoi(part);
        if (val < 0 || val > 255) return false;
    }
    return count == 4;
}

int main() {
    std::cout << "Valid IP? " << (isValidIP("172.16.254.1") ? "Yes" : "No") << std::endl;
    return 0;
}
```
