# 42 | Frequency-Based Compression

Compress data by mapping symbols to their frequencies.

---

## 1. The Objective
Given a list of items, represent them as a frequency map to save space (e.g., for transmission).

---

## 2. Visual Logic
### The "Registry" Strategy
Original: `[apple, apple, orange, banana, apple]` (Storage: 5 large strings)
Compressed: `apple:3, orange:1, banana:1` (Storage: 3 strings + 3 ints)

---

## 3. The "Aha!" Moment
This is the core idea behind **Huffman Coding** and entropy-based compression. If an item repeats, you only store the item once and track its occurrences.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <string>
#include <unordered_map>

void compressData(const std::vector<std::string>& data) {
    std::unordered_map<std::string, int> registry;
    for (const std::string& item : data) registry[item]++;
    
    std::cout << "Compressed Stream:" << std::endl;
    for (auto const& [item, count] : registry) {
        std::cout << item << ":" << count << " ";
    }
}

int main() {
    std::vector<std::string> stream = {"log", "error", "log", "warn", "log"};
    compressData(stream);
    return 0;
}
```
