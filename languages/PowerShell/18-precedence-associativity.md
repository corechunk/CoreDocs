# Template: Precedence & Associativity [CORE]

**Goal:** To define the order of operations in PowerShell.

---

## 1. Pwsh 5.1 / 7+ (Common)
```powershell
# Parentheses first
$res = (1 + 2) * 3 # 9
```

## 2. Portable Path
```powershell
# Comparison before Logic
$res = $a -eq 1 -and $b -eq 2
```

## 3. Explicit Path
```powershell
# Explicit grouping for complex filters
if (($a -gt 10) -and (($b -lt 5) -or ($c -eq 0))) { }
```

# The Logic Bridge
// Logic: PowerShell follows standard mathematical precedence but gives high priority to the pipeline operator (`|`).
