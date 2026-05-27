# Template: Pattern Matching [PRO]

**Goal:** To define `-like` (Wildcard) and `-match` (Regex) operators.

---

## 1. Pwsh 5.1 / 7+ (Common)
```powershell
"file.txt" -like "*.txt" # Wildcard
"123" -match "^\d+$" # Regex
```

## 2. Portable Path
```powershell
# Capturing regex groups
if ("user:gemini" -match "user:(?<name>.*)") {
    $matches['name'] # Output: gemini
}
```

## 3. Explicit Path (7+ Regex Options)
```powershell
[regex]::Match("data", "DA", [System.Text.RegularExpressions.RegexOptions]::IgnoreCase)
```

# The Logic Bridge
// Logic: `-match` populates the automatic `$Matches` hashtable upon a successful hit.
