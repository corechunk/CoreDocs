# Minimum Spanning Trees (MST)

## Explanation
A Minimum Spanning Tree of a connected, undirected graph is a subgraph that is a tree and connects all the vertices together with the minimum possible total edge weight.

## Algorithms
- **Kruskal’s Algorithm**: A greedy algorithm that sorts all edges and adds them one by one if they don't form a cycle (uses DSU).
- **Prim’s Algorithm**: A greedy algorithm that starts from a vertex and grows the MST by adding the cheapest edge from the tree to a vertex not yet in the tree.

## Complexity Analysis
- **Kruskal**: O(E log E) or O(E log V) due to sorting.
- **Prim**: O(E log V) with a priority queue.
