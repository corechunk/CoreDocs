# Topological Sorting

## Explanation
A linear ordering of vertices in a Directed Acyclic Graph (DAG) such that for every directed edge `uv`, vertex `u` comes before `v` in the ordering.

## Algorithms
- **Kahn’s Algorithm**: Based on in-degrees of vertices (BFS-like).
- **DFS-based**: Using a stack and the finish times of nodes.

## Complexity Analysis
- **Time Complexity**: O(V + E).
- **Space Complexity**: O(V).
