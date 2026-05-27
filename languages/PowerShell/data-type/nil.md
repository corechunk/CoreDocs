# Template: Nulls ($null) [CORE]

**Goal:** To define the `$null` value and the behavior of the "Null-Coalescing" operator.

---

## 1. Pwsh 5.1 (Legacy)
```powershell
if ($null -eq $var) { $var = "Default" }
```

## 2. Pwsh 7+ (Modern)
```powershell
# Null-coalescing (7.1+)
$var = $var ?? "Default"
```

## 3. Portable Path
```powershell
# Explicit null check
if ($var -eq $null) { Write-Warning "Value is null" }
```

## 4. Explicit Path
```powershell
[Nullable[int]]$age = $null
```

# The Logic Bridge
// Logic: `$null` represents the absence of an object; in PowerShell, it's safer to compare it on the left side to avoid collection-filtering side effects.
