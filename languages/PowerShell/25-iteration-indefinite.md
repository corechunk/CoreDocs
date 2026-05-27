# Template: Iteration (Indefinite) [CORE]

**Goal:** To define `while`, `do..while`, and `do..until`.

---

## 1. Pwsh 5.1 / 7+ (Common)
```powershell
$i = 0
while ($i -lt 5) { $i++ }
```

## 2. Portable Path
```powershell
do {
    $i--
} while ($i -gt 0)
```

## 3. Explicit Path
```powershell
do {
    "Wait"
} until (Test-Path "file.txt")
```

# The Logic Bridge
// Logic: `until` is the inverse of `while`; it runs as long as the condition is FALSE.
