# Template: Native Strings [PRO]

**Goal:** To define Pwsh-specific string manipulation (Slicing, `-replace`, `-split`).

---

## 1. Pwsh 5.1 (Legacy)
```powershell
$str = "Hello World"
$str.Substring(0, 5)
```

## 2. Pwsh 7+ (Modern Slicing)
```powershell
# 7+ supports negative indices in some .NET methods
"abcdef"[0..2] # Output: a, b, c (Array of chars)
```

## 3. Portable Path
```powershell
# The Pwsh way (Regex based replace)
"apple" -replace "a", "A"
```

## 4. Explicit Path
```powershell
[string[]]$parts = "a,b,c" -split ","
```

# The Logic Bridge
// Logic: Operators like `-replace` and `-split` are case-insensitive by default in PowerShell, unlike standard .NET methods.
