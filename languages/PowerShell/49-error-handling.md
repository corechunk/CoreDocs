# Template: Error Handling [CORE]

**Goal:** To define `try..catch` and `$Error`.

---

## 1. Pwsh 5.1 / 7+ (Common)
```powershell
try {
    Get-Item "non_existent" -ErrorAction Stop
} catch {
    "Caught: $($_.Exception.Message)"
}
```

## 2. Portable Path
```powershell
# Accessing the last error
$Error[0]
```

## 3. Explicit Path
```powershell
trap { "Trapped: $_"; continue }
1 / 0
```

# The Logic Bridge
// Logic: Commands must have `-ErrorAction Stop` to be catchable in a `try` block; otherwise, they only emit a non-terminating error to the stream.
