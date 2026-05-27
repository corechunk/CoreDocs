# Template: Syntactic Automation [SYSTEMS]

**Goal:** To define Proxy Functions and Dynamic Parameters.

---

## 1. Pwsh 5.1 (Legacy)
```powershell
# Creating an alias to an external tool
function ls { Get-ChildItem @args }
```

## 2. Pwsh 7+ (Modern)
```powershell
# Using the Pipeline Chain operators (7.0+)
Get-Date && Write-Host "Success"
```

## 3. Portable Path
```powershell
# Splatting (Automated parameter passing)
$params = @{ Path = "C:\"; Filter = "*.txt" }
Get-ChildItem @params
```

## 4. Explicit Path
```powershell
# Dynamic parameters based on runtime logic
DynamicParam { }
```

# The Logic Bridge
// Logic: "Splatting" converts a hashtable into a set of named parameters, reducing "wall-of-code" command calls.
