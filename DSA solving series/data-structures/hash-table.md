# 🔑 Hashing & Hash Tables

## 1. The Objective
A Hash Table is a data structure that maps **Keys** to **Values** using a **Hash Function**. It is designed to provide **$O(1)$** average-case performance for search, insertion, and deletion, making it the fastest structure for key-based retrieval.

---

## 2. Visual Logic
### The Mapping Process
```text
Key: "Apple"  --[ Hash Function ]--> Index: 4
Key: "Banana" --[ Hash Function ]--> Index: 7

Array: [ 0 | 1 | 2 | 3 | "Apple" | 5 | 6 | "Banana" ]
```

### Collision Resolution
- **Chaining:** Each bucket points to a linked list of entries.
- **Open Addressing:** If index `i` is full, try `i+1` (Linear Probing).

---

## 3. The Logic Bridge
- **The "Magic" of Hashing:** We convert infinite possible keys (like all strings) into a finite set of array indices. 
- **The Birthday Paradox:** Collisions are inevitable. The quality of a hash table depends on how it handles collisions and how "uniform" its hash function is.
- **Load Factor:** When the table is more than ~70% full, performance drops. We then **Rehash** (resize the array and re-map all keys) to maintain $O(1)$ speed.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Abstract Chaining)

```cpp
#include <iostream>
#include <vector>
#include <list>

class HashTable {
    int size;
    std::vector<std::list<std::string>> table;

public:
    HashTable(int s) : size(s) { table.resize(size); }

    int hash(std::string key) {
        int h = 0;
        for (char c : key) h += c;
        return h % size;
    }

    void insert(std::string key) {
        table[hash(key)].push_back(key);
    }

    bool search(std::string key) {
        for (auto x : table[hash(key)]) {
            if (x == key) return true;
        }
        return false;
    }
};

int main() {
    HashTable ht(10);
    ht.insert("code");
    ht.insert("chunk");
    std::cout << "Contains 'code': " << ht.search("code") << std::endl;
    return 0;
}
```

---
[➔ Back to Roadmap](../DSA-Master-Roadmap.md)
