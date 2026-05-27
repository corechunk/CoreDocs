# Template: Iteration (Definite) [CORE]

**Goal:** To define `foreach` and `for`.

---

## 1. Pwsh 5.1 / 7+ (Common)
```powershell
foreach ($item in 1..5) { $item }
```

## 2. Portable Path (Pipeline Foreach)
```powershell
1..5 | ForEach-Object { $_ * 2 }
```

## 3. Explicit Path (C-Style For)
```powershell
for ($i = 0; $i -lt 5; $i++) {
    Write-Output "Index: $i"
}
```

# The Logic Bridge
// Logic: `foreach` (statement) is faster as it loads the whole collection into memory; `ForEach-Object` (cmdlet) uses the pipeline and is more memory-efficient for large data.
