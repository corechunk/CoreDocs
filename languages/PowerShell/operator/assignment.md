# Template: Assignment Operators [CORE]

**Goal:** To define `=`, `+=`, `-=`, and `++`.

---

## 1. Pwsh 5.1 / 7+ (Common)
```powershell
$i = 0
$i++ # 1
$msg = "Hello"
$msg += " World"
```

## 2. Portable Path
```powershell
# Multi-assignment
$a, $b = 1, 2
```

## 3. Explicit Path (7+ Null-Assignment)
```powershell
# Assign only if null (7.1+)
$config ??= "Default"
```

# The Logic Bridge
// Logic: `+=` on arrays creates a NEW array (performance hit), whereas on strings it performs concatenation.
