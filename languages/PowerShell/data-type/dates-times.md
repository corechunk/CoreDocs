# Template: Dates & Times [CORE]

**Goal:** To define `[datetime]` and `[timespan]`.

---

## 1. Pwsh 5.1 / 7+ (Common)
```powershell
$now = Get-Date
$later = $now.AddDays(1)
```

## 2. Portable Path
```powershell
# Time difference
$diff = (New-TimeSpan -Days 1)
```

## 3. Explicit Path
```powershell
[datetime]$birthDay = "1990-01-01"
[timespan]$timeout = "00:05:00" # 5 minutes
```

# The Logic Bridge
// Logic: `[datetime]` maps to `System.DateTime`, providing powerful calendar math via .NET methods.
