# Hash Tables

## Explanation
A Hash Table (or Hash Map) is a data structure that maps keys to values using a hash function. It provides efficient data retrieval by computing an index from the key.

## Key Concepts
- **Hash Function**: Maps a key to an integer index.
- **Collision Resolution**: Handling cases where two keys hash to the same index (e.g., Chaining, Open Addressing).
- **Load Factor**: The ratio of the number of elements to the size of the table.

## Common Methods/Actions
- **insert(key, value)**: Adds a key-value pair. Average O(1).
- **get(key)**: Retrieves the value associated with a key. Average O(1).
- **delete(key)**: Removes a key-value pair. Average O(1).
- **contains(key)**: Checks if a key exists in the table.
