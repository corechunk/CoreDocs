# 🧬 Static Single Assignment (SSA) Form

## 1. SSA Invariant
In Static Single Assignment (SSA) form, every variable is assigned exactly once. Multiple assignments to a variable in source code generate distinct versioned symbols (`x1`, `x2`, `x3`).

## 2. Phi ($\phi$) Functions & Dominance Frontiers
When branching control paths merge (e.g., after an `if`/`else` block), compilers insert **$\phi$ (Phi) functions** at dominance join points to select the correct variable version based on the incoming execution path.
