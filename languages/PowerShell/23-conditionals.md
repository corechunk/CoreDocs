# Template: Conditionals [CORE]

**Goal:** To define `if`, `else`, and `switch`.

---

## 1. Pwsh 5.1 / 7+ (Common)
```powershell
if ($a -gt 10) { "High" } else { "Low" }
```

## 2. Portable Path (Switch)
```powershell
switch ($val) {
    1 { "One" }
    2 { "Two" }
    Default { "Other" }
}
```

## 3. Explicit Path (7+ Ternary)
```powershell
$status = ($a -eq 1) ? "OK" : "Error"
```

# The Logic Bridge
// Logic: The `switch` statement in PowerShell is a powerful iterative construct; it can process entire arrays without a loop.
