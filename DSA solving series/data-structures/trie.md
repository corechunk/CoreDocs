# 🏗️ Trie (Prefix Tree)

## 1. The Objective
A Trie is an efficient information retrieval data structure. It is used to store a dynamic set or associative array where the keys are usually strings. It excels at **prefix matching** and predictive text.

---

## 2. Visual Logic
### Storing "CAT", "CAR", "DOG"
```text
       (root)
      /      \
    [C]      [D]
     |        |
    [A]      [O]
    / \       |
  [T] [R]    [G]*
   *   *
```
- `*` denotes the end of a word.
- Words sharing a common prefix share the same nodes.

---

## 3. The Logic Bridge
- **Space-Time Tradeoff:** Tries use more memory than hash tables (due to many pointers) but provide **$O(L)$ search time** where $L$ is the length of the word, regardless of how many words are in the Trie.
- **Prefix Power:** You can find all words starting with "CA" in just $O(L)$ time, which is impossible with a standard Hash Table ($O(N)$ scan required).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Standard Trie)

```cpp
#include <iostream>
#include <vector>

struct TrieNode {
    TrieNode* children[26];
    bool isEndOfWord;
    TrieNode() {
        for (int i = 0; i < 26; i++) children[i] = nullptr;
        isEndOfWord = false;
    }
};

void insert(TrieNode* root, std::string word) {
    TrieNode* curr = root;
    for (char ch : word) {
        int idx = ch - 'a';
        if (!curr->children[idx]) curr->children[idx] = new TrieNode();
        curr = curr->children[idx];
    }
    curr->isEndOfWord = true;
}

bool search(TrieNode* root, std::string word) {
    TrieNode* curr = root;
    for (char ch : word) {
        int idx = ch - 'a';
        if (!curr->children[idx]) return false;
        curr = curr->children[idx];
    }
    return curr->isEndOfWord;
}

int main() {
    TrieNode* root = new TrieNode();
    insert(root, "cat");
    std::cout << "Searching 'cat': " << search(root, "cat") << std::endl;
    std::cout << "Searching 'car': " << search(root, "car") << std::endl;
    return 0;
}
```

---
[➔ Back to Tree Hub](tree.md) | [➔ Back to Roadmap](../DSA-Master-Roadmap.md)
