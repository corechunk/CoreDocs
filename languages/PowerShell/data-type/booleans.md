# Template: Booleans [CORE]

**Goal:** To define the `$true` and `$false` automatic variables.

---

## 1. Pwsh 5.1 / 7+ (Common)
```powershell
$isOk = $true
if ($isOk) { "Success" }
```

## 2. Portable Path
```powershell
# Always place $null or $true/false on the left in comparisons
if ($true -eq $isOk) { "Correct" }
```

## 3. Explicit Path
```powershell
[bool]$flag = 1 # Coerces to $true
```

# The Logic Bridge
// Logic: Boolean variables are instances of `System.Boolean`.
