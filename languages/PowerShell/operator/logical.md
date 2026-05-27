# Template: Logical Operators [CORE]

**Goal:** To define `-and`, `-or`, `-not`, and `!`.

---

## 1. Pwsh 5.1 / 7+ (Common)
```powershell
if ($true -and $false) { "Never" }
if (-not $false) { "True" }
```

## 2. Portable Path
```powershell
# Short-circuiting behavior
if ($a -or (Test-Connection google.com)) { }
```

## 3. Explicit Path
```powershell
[bool]$res = ($a -eq 1) -and ($b -eq 2)
```

# The Logic Bridge
// Logic: Logical operators work on booleans or types that can be coerced to booleans.
