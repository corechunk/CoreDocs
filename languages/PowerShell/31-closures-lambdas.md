# Template: Closures & Lambdas [PRO]

**Goal:** To define ScriptBlocks and their variable capture behavior.

---

## 1. Pwsh 5.1 (Legacy)
```powershell
$x = 10
$sb = { $x }.GetNewClosure()
$x = 20
& $sb # Output: 10
```

## 2. Pwsh 7+ (Modern)
```powershell
# Using ScriptBlocks as delegates
$list = 1..5
$list | ForEach-Object { $_ * 2 }
```

## 3. Portable Path
```powershell
$sb = { param($val) $val + $script:outer }
```

## 4. Explicit Path
```powershell
[Func[int, int]]$lambda = { param($i) $i * $i }
```

# The Logic Bridge
// Logic: ScriptBlocks do not capture their environment by default; you must call `GetNewClosure()` to "freeze" the current local variables.
