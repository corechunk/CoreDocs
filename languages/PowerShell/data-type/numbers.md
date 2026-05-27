# Template: Numbers [CORE]

**Goal:** To define integers, decimals, and hex literals in PowerShell.

---

## 1. Pwsh 5.1 (Legacy)
```powershell
$dec = 10.5
$hex = 0x10 # 16
```

## 2. Pwsh 7+ (Modern Suffixes)
```powershell
# Support for binary and larger types
$bin = 0b1010
$long = 100L
$decimal = 100d
```

## 3. Portable Path
```powershell
$num = 100
$isNumber = $num.GetType().IsPrimitive
```

## 4. Explicit Path
```powershell
[int]$i = 10
[long]$l = 100L
[double]$d = 1.23
[decimal]$dec = 1.23d
[byte]$b = 255
[int64]$bigInt = 9223372036854775807
```

# The Logic Bridge
// Logic: PowerShell uses .NET's math engine, allowing it to handle arbitrary precision through `[bigint]` and `[decimal]`; suffixes (`L`, `d`, `n`) tell the parser which .NET type to instantiate.
