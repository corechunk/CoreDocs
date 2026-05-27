# Template: Array Lists [PRO]

**Goal:** To define high-performance list manipulation.

---

## 1. Pwsh 5.1 (Legacy)
```powershell
$list = New-Object System.Collections.ArrayList
[void]$list.Add(1)
$list.Remove(1)
```

## 2. Pwsh 7+ (Modern)
```powershell
# Using modern .NET constructor
$list = [System.Collections.Generic.List[string]]::new()
$list.AddRange(@("a", "b", "c"))
```

## 3. Portable Path
```powershell
$list = @()
# Using the pipeline for filtering
$filtered = $list | Where-Object { $_ -ne $null }
```

## 4. Explicit Path
```powershell
[System.Collections.Generic.List[int]]$nums = 1..10
```

# The Logic Bridge
// Logic: `ArrayList` is non-generic (stores `object`), while `List<T>` is type-safe and avoids "boxing" overhead for value types.
