# Template: Strings & Characters [CORE]

**Goal:** To define the `[string]` and `[char]` types.

---

## 1. Pwsh 5.1 / 7+ (Common)
```powershell
$s = "A string"
$c = 'A' # Still a string by default
```

## 2. Portable Path
```powershell
# Casting string to char
$char = [char]"A"
```

## 3. Explicit Path
```powershell
[string]$msg = "Explicit String"
[char]$letter = 'Z'
[char[]]$alphabet = "ABC" -tochararray()
```

# The Logic Bridge
// Logic: PowerShell treats everything as a string unless explicitly cast to `[char]`; `[string]` is an alias for `System.String`.
