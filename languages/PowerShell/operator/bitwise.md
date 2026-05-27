# Template: Bitwise Operators [CORE]

**Goal:** To define bitwise logic using `-band`, `-bor`, `-bxor`, and `-bnot`.

---

## 1. Pwsh 5.1 / 7+ (Common)
```powershell
# Bitwise AND
10 -band 7 # 2
```

## 2. Pwsh 7+ (Modern bit-shifts)
```powershell
# Shift operators (7.0+)
1 -shl 3 # 8 (1 << 3)
8 -shr 2 # 2 (8 >> 2)
```

## 3. Portable Path
```powershell
# Portable bit-shift via .NET
[int]$val = 1
[int]$res = $val * [Math]::Pow(2, 3) # Shift left 3
```

## 4. Explicit Path
```powershell
[uint32]$mask = 0xFFFF0000
```

# The Logic Bridge
// Logic: Prior to Pwsh 7, bit-shifting required either math multiplication or raw .NET calls; 7+ added native `shl/shr` operators.
