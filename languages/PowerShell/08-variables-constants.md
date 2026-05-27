# Template: Variables & Constants [CORE]

**Goal:** To define the sigil-based variable system (`$`) and the methods for creating read-only constants.

---

## 1. The Definition (Mental Model)
PowerShell variables are prefixes with `$`. They are dynamically typed by default but act as labels for .NET objects. PowerShell does not have a native `const` keyword; instead, it uses the `Set-Variable` command with options.

## 1. Pwsh 5.1 (Legacy)
```powershell
$var = "Data"
# Standard RO (Can be removed with -Force)
Set-Variable -Name "MY_CONST" -Value 100 -Option ReadOnly
```

## 2. Pwsh 7+ (Modern)
```powershell
# Using modern syntax for variables
$name = "Modern"
# Persistent RO in a session
Set-Variable -Name "STATUS" -Value "Active" -Option Constant
```

## 3. Portable Path
```powershell
# Safe variable initialization across versions
$data = "Common"
if ($null -eq $global:config) { $global:config = @{} }
```

## 4. Explicit Path (7+ Strict Typing)
```powershell
[string]$userName = "Admin"
[int]$maxRetry = 5
# Using [ReadOnlyVariable] logic via Type Acceleration
```

# The Logic Bridge
// Logic: PowerShell variables live in specific scopes (Local, Script, Global, Private); scoping is managed via the `Variable:` drive.
