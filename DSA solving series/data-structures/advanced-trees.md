# Advanced Trees

## Explanation
Specialized tree structures designed for specific types of queries or data.

## Types
- **Trie (Prefix Tree)**: Used for storing strings and efficient prefix matching.
- **Segment Tree**: Used for range queries (e.g., sum, min/max in a range) and updates in O(log n).
- **Fenwick Tree (Binary Indexed Tree)**: Similar to Segment Trees but more space-efficient and easier to implement for prefix sums.

## Common Methods/Actions
- **Trie - insert(word)**: Adds a word to the trie.
- **Trie - search(prefix)**: Checks if any word starts with the given prefix.
- **Segment Tree - build(array)**: Constructs the tree from an array.
- **Segment Tree - update(index, val)**: Updates an element and its relevant range nodes.
- **Segment Tree - query(l, r)**: Performs a range query.
