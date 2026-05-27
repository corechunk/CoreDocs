# Template: Jump Statements [PRO]

**Goal:** To define `break`, `continue`, and `return`.

---

## 1. Pwsh 5.1 / 7+ (Common)
```powershell
foreach ($i in 1..10) {
    if ($i -eq 5) { break }
    if ($i % 2 -eq 0) { continue }
    $i
}
```

## 2. Portable Path (Labeled Loops)
```powershell
:Outer foreach ($i in 1..3) {
    foreach ($j in 1..3) {
        if ($j -eq 2) { break Outer }
    }
}
```

## 3. Explicit Path
```powershell
function Test {
    return "Result"
}
```

# The Logic Bridge
// Logic: `return` in PowerShell is often misused; it doesn't just return a value, it exits the function. Any uncaptured output from previous lines is also returned.
