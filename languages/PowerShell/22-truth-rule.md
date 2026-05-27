# Template: Truth Rule [CORE]

**Goal:** To define what evaluates to `$true` and `$false`.

---

## 1. Pwsh 5.1 / 7+ (Common)
```powershell
# FALSE values:
if ($false) { }
if ($null) { }
if (0) { }
if ("") { }
if (@()) { }

# TRUE values:
if (1) { "True" }
if ("text") { "True" }
```

## 2. Portable Path
```powershell
# Explicitly checking for empty collection
$list = @()
if ($list.Count -gt 0) { "Not Empty" }
```

## 3. Explicit Path (7+ Strict Logic)
```powershell
[bool]$isValid = [bool](Get-Process -Name "non-existent" -ErrorAction SilentlyContinue)
```

# The Logic Bridge
// Logic: Empty collections (`@()`) are falsey in PowerShell, which is a major difference from many other languages.
