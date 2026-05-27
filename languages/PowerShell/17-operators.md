# Template: Operators [CORE]

**Goal:** To define the comparison-first operator syntax (e.g., `-eq` vs `==`).

---

## 1. The Definition (Mental Model)
PowerShell uses word-based operators to avoid ambiguity with redirection symbols (`>`).
- **Comparison:** `-eq`, `-ne`, `-gt`, `-lt`.
- **Logical:** `-and`, `-or`, `-not`.
- **Arithmetic:** `+`, `-`, `*`, `/`.

- **Math:** [math.md](./operator/math.md)
- **Logical:** [logical.md](./operator/logical.md)
- **Bitwise:** [bitwise.md](./operator/bitwise.md)
- **Assignment:** [assignment.md](./operator/assignment.md)

## 1. Pwsh 5.1 / 7+ (Common)
```powershell
$a = 10
if ($a -eq 10) { "Equal" }
```

## 2. Portable Path
```powershell
# Using -contains for arrays
$list = 1,2,3
$list -contains 2 # Output: True
```

## 3. Explicit Path (7+ Ternary)
```powershell
$res = ($a -gt 5) ? "High" : "Low"
```

# The Logic Bridge
// Logic: Comparison operators are case-insensitive by default (`-eq`). Use `-ceq` for case-sensitive comparison.
