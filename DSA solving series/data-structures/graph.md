# Graphs

## Explanation
A Graph consists of a set of vertices (nodes) and a set of edges connecting pairs of vertices.

## Representations
- **Adjacency Matrix**: A 2D array where `matrix[i][j]` is 1 if there is an edge from vertex `i` to `j`.
- **Adjacency List**: An array of lists, where `list[i]` contains all vertices adjacent to vertex `i`.

## Types
- **Directed/Undirected**: Whether edges have a direction.
- **Weighted/Unweighted**: Whether edges have associated costs.
- **DAG**: Directed Acyclic Graph.

## Common Methods/Actions
- **addEdge(u, v)**: Connects vertices `u` and `v`.
- **removeEdge(u, v)**: Removes the connection.
- **hasEdge(u, v)**: Checks if `u` and `v` are connected.
- **getNeighbors(u)**: Returns all vertices adjacent to `u`.
