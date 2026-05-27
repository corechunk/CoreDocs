# Template: Math Operators [CORE]

**Goal:** To define arithmetic operations and .NET math integration.

---

## 1. Pwsh 5.1 / 7+ (Common)
```powershell
$sum = 1 + 1
$mod = 10 % 3 # 1
```

## 2. Portable Path
```powershell
# Using [Math] library for advanced ops
[Math]::Pow(2, 3) # 8
[Math]::Sqrt(16) # 4
```

## 3. Explicit Path (7+ BigInt)
```powershell
[bigint]$large = [Math]::Pow(2, 64)
```

# The Logic Bridge
// Logic: PowerShell auto-upcasts integers to doubles or decimals if the result exceeds the current type's capacity.
