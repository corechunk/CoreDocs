# Template: Expressions & Statements [CORE]

**Goal:** To define the difference between a command call and an expression.

---

## 1. Pwsh 5.1 / 7+ (Common)
```powershell
# Statement
Get-Process

# Expression (Value-returning)
$a = 1 + 1
```

## 2. Portable Path
```powershell
# Capturing a statement result in an expression
$data = (Get-Service | Select-Object -First 5)
```

## 3. Explicit Path
```powershell
# Using the array sub-expression @()
[array]$list = @(Get-ChildItem)
```

# The Logic Bridge
// Logic: In PowerShell, almost everything is an expression because most statements return objects to the pipeline.
