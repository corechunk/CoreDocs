# Template: Command Substitution [PRO]

**Goal:** To define the `$()` operator and capturing output.

---

## 1. Pwsh 5.1 / 7+ (Common)
```powershell
$date = $(Get-Date)
"Current year: $($date.Year)"
```

## 2. Portable Path
```powershell
# Capturing external command output
$files = $(ls -1)
```

## 3. Explicit Path
```powershell
[string]$out = $(cmd.exe /c "echo raw")
```

# The Logic Bridge
// Logic: `$()` creates a sub-expression that executes and places the resulting objects back into the string or variable.
