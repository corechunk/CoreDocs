# Disjoint Set Union (Union-Find)

## Explanation
A data structure that keeps track of a set of elements partitioned into a number of disjoint (non-overlapping) subsets.

## Common Methods/Actions
- **find(i)**: Determines which subset `i` belongs to. Often includes "path compression" for optimization.
- **union(i, j)**: Joins two subsets into a single subset. Often includes "union by rank/size" for optimization.
- **makeSet(n)**: Initializes `n` disjoint sets, each containing one element.
