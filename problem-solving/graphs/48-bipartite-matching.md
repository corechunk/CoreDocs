# 48 | Bipartite Matching

Find the maximum number of pairs between two sets.

---

## 1. The Objective
Match $N$ jobs to $M$ applicants based on preferences.

---

## 2. Visual Logic
### The "Flow" Reduction
Create a Source node connected to all Applicants, and a Sink node connected to all Jobs. The max flow from Source to Sink is the max matching.

---

## 3. The "Aha!" Moment
Bipartite matching is a specific application of **Max Flow**.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
// Specialist algorithm: Hopcroft-Karp or augmenting paths DFS.
```
