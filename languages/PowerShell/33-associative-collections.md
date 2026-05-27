# Template: Associative Collections [CORE]

**Goal:** To define Hashtables (`@{}`) and Ordered Dictionaries.

---

## 1. Pwsh 5.1 / 7+ (Common)
```powershell
$map = @{
    Key1 = "Val1"
    Key2 = 100
}
$map['Key1']
```

## 2. Portable Path (Ordered)
```powershell
# Preserves insertion order
$ordered = [ordered]@{
    A = 1
    B = 2
}
```

## 3. Explicit Path (7+ Generic Dictionary)
```powershell
$dict = [System.Collections.Generic.Dictionary[string, int]]::new()
$dict.Add("One", 1)
```

# The Logic Bridge
// Logic: Hashtables in PowerShell are case-insensitive by default. Use `[System.Collections.Hashtable]::new()` for case-sensitive keys.
