# Template: Tokens & Lexemes [CORE]

**Goal:** To define the atoms of PowerShell: Cmdlets, Aliases, and the Verb-Noun pattern.

---

## 1. The Definition (Mental Model)
PowerShell uses a **Verb-Noun** naming convention (e.g., `Get-Process`).
- **Command:** The full Verb-Noun.
- **Alias:** A shorthand (e.g., `ls` for `Get-ChildItem`).
- **Parameter:** Prefixed with `-` (e.g., `-Path`).

## 1. Pwsh 5.1 (Legacy)
```powershell
# Using an alias
ls C:\
```

## 2. Pwsh 7+ (Modern)
```powershell
# Using the full Cmdlet (Best practice)
Get-ChildItem -Path /home/user/
```

## 3. Portable Path
```powershell
$files = Get-ChildItem -Path "."
# Output: (List of files)
```

## 4. Explicit Path (Fully Qualified)
```powershell
Microsoft.PowerShell.Management\Get-ChildItem -LiteralPath "." -ErrorAction Stop
```

# The Logic Bridge
// Logic: Aliases are for the interactive CLI; full Cmdlet names are for production scripts to ensure readability and version stability.
