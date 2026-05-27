# Network Flow

## Explanation
Deals with finding the maximum amount of "flow" that can pass through a network from a source node to a sink node.

## Algorithms
- **Ford-Fulkerson Method**: Uses augmenting paths to increase flow.
- **Edmonds-Karp Algorithm**: An implementation of Ford-Fulkerson using BFS.

## Complexity Analysis
- **Ford-Fulkerson**: O(E * max_flow).
- **Edmonds-Karp**: O(V * E^2).
