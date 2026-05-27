# 12 | Palindrome Number

Check if a number reads the same forwards and backwards.

---

## 1. The Objective
Given `121`, return `true`. Given `123`, return `false`.

---

## 2. Visual Logic
### The Mirror Strategy
1. Take the original number.
2. Create its reverse (see problem 11).
3. If `Original == Reverse`, it's a palindrome.

```text
Original: 121
Reverse:  121
121 == 121 -> SUCCESS
```

---

## 3. The "Aha!" Moment
A palindrome is simply a number that is equal to its own reverse. **Crucial:** You must store the original number in a temporary variable because the reversal process destroys the original (by dividing it to 0).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy A: Reverse and Compare
 */
bool isPalindrome(long long n) {
    if (n < 0) return false; // Negative numbers are not palindromes (due to '-')
    
    long long original = n;
    long long reversed = 0;
    
    while (n > 0) {
        reversed = (reversed * 10) + (n % 10);
        n /= 10;
    }
    
    return original == reversed;
}

int main() {
    int num = 12321;
    
    if (isPalindrome(num)) {
        std::cout << num << " is a Palindrome." << std::endl;
    } else {
        std::cout << num << " is NOT a Palindrome." << std::endl;
    }
    
    return 0;
}
```
