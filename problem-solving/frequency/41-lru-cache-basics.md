# 41 | LRU Cache Basics

Implement the core logic of a Least Recently Used (LRU) Cache.

---

## 1. The Objective
Create a system that stores key-value pairs with a fixed capacity. When full, it should discard the item that hasn't been accessed for the longest time.

---

## 2. Visual Logic
### The "List + Map" Duo
1. **HashMap:** For $O(1)$ lookups: `key -> iterator in list`.
2. **Doubly Linked List:** For $O(1)$ reordering: Store keys in order of usage.
   - When a key is used, move it to the **Front**.
   - When capacity exceeded, remove the **Back** item.

---

## 3. The "Aha!" Moment
A Map provides **Speed**, but a List provides **History**. Combining them allows you to track usage time without searching through the entire dataset.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <list>
#include <unordered_map>

class LRUCache {
    int capacity;
    std::list<int> lru;
    std::unordered_map<int, std::pair<int, std::list<int>::iterator>> cache;

public:
    LRUCache(int cap) : capacity(cap) {}

    int get(int key) {
        if (!cache.count(key)) return -1;
        lru.erase(cache[key].second);
        lru.push_front(key);
        cache[key].second = lru.begin();
        return cache[key].first;
    }

    void put(int key, int value) {
        if (cache.count(key)) {
            lru.erase(cache[key].second);
        } else if (lru.size() == capacity) {
            cache.erase(lru.back());
            lru.pop_back();
        }
        lru.push_front(key);
        cache[key] = {value, lru.begin()};
    }
};

int main() {
    LRUCache c(2);
    c.put(1, 1); c.put(2, 2);
    std::cout << c.get(1) << std::endl; // 1
    c.put(3, 3); // evicts key 2
    std::cout << c.get(2) << std::endl; // -1
    return 0;
}
```
