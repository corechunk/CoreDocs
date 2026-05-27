# Template: Sequential Collections [CORE]

**Goal:** To define Arrays (`@()`) and the shift to `System.Collections.Generic.List`.

---

## 1. Pwsh 5.1 (Legacy Array)
```powershell
$arr = 1, 2, 3
$arr += 4 # PERFORMANCE WARNING: Creates new array
```

## 2. Pwsh 7+ (Modern List)
```powershell
# Using the generic list for performance
$list = [System.Collections.Generic.List[int]]::new()
$list.Add(10)
```

## 3. Portable Path
```powershell
# ArrayList (Portable but legacy .NET)
$list = New-Object System.Collections.ArrayList
[void]$list.Add("Data")
```

## 4. Explicit Path
```powershell
[int[]]$staticArr = 1, 2, 3
```

# The Logic Bridge
// Logic: The `+=` operator on a standard array is an $O(n)$ operation because arrays in .NET have a fixed size; generic Lists are $O(1)$ for additions.
