# 🎨 Chaitin-Briggs Graph Coloring Register Allocation

## 1. Interference Graph Construction
Builds an interference graph where nodes represent virtual variables and undirected edges connect variables whose live ranges overlap concurrently.

## 2. K-Coloring Reduction
Attempts to color the graph using $K$ colors (where $K$ equals the number of physical CPU registers). Graph coloring produces optimal register assignments for release AOT production builds.
