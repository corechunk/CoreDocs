# 🌸 Bloom Filter (Probabilistic)

## 1. The Objective
A Bloom Filter is a space-efficient **probabilistic** data structure used to test whether an element is a member of a set. It can tell you "Definitely Not" or "Maybe Yes", but never "Definitely Yes".

---

## 2. Visual Logic
### Hash Array (Bits)
```text
Array: [ 0 | 1 | 0 | 0 | 1 | 1 | 0 ]
         0   1   2   3   4   5   6
```
1. To **Add** an element, hash it with $K$ different functions and set those bits to `1`.
2. To **Query**, hash it with $K$ functions. If any of those bits are `0`, the element is **Definitely Not** in the set.

---

## 3. The Logic Bridge
- **The "False Positive" Tradeoff:** Because multiple elements might hash to the same bits, you might get a "Yes" for an item that was never added. However, you will **never** get a false negative (if it's not there, it says no).
- **Extreme Space Efficiency:** You can represent a set of billions of items in a few megabytes. Used in **Web Browsers** (checking malicious URLs) and **Databases** (avoiding expensive disk seeks for non-existent keys).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Abstract Concept)

```cpp
#include <iostream>
#include <vector>
#include <bitset>

class BloomFilter {
    std::bitset<1000> bits;

public:
    void add(std::string s) {
        bits.set(std::hash<std::string>{}(s) % 1000);
        // In real life, use multiple hash functions
    }

    bool contains(std::string s) {
        return bits.test(std::hash<std::string>{}(s) % 1000);
    }
};

int main() {
    BloomFilter bf;
    bf.add("hello");
    std::cout << "Contains 'hello': " << bf.contains("hello") << std::endl;
    std::cout << "Contains 'world': " << bf.contains("world") << std::endl;
    return 0;
}
```

---
[➔ Back to Hashing Hub](hash-table.md) | [➔ Back to Roadmap](../DSA-Master-Roadmap.md)
