# Template: String Escaping [CORE]

**Goal:** To define the backtick (`` ` ``) as the escape character.

---

## 1. Pwsh 5.1 (Legacy)
```powershell
$msg = "Line1`nLine2" # Newline
$tab = "Data`tSeparated" # Tab
```

## 2. Pwsh 7+ (Modern)
```powershell
# Supporting ANSI escape sequences natively
$red = "`e[31mRedText`e[0m"
```

## 3. Portable Path
```powershell
# Standard escaping
$quote = "He said, `"Hello`""
```

## 4. Explicit Path
```powershell
[string]$path = 'C:\Temp' # Single quotes prevent expansion
```

# The Logic Bridge
// Logic: Double quotes (`"`) allow variable expansion and escape sequences; single quotes (`'`) are literal.
