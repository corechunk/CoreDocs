# Template: Passing Mechanisms [CORE]

**Goal:** To define Value vs. Reference passing.

---

## 1. The Definition (Mental Model)
- **Value Types:** Numbers, Booleans, Strings (Mostly).
- **Reference Types:** Arrays, Hashtables, Objects.

## 1. Pwsh 5.1 / 7+ (Common)
```powershell
function Update-Hash($h) {
    $h.Key = "Updated" # Affects original
}

$myHash = @{ Key = "Original" }
Update-Hash $myHash
# $myHash.Key is now "Updated"
```

## 2. Portable Path
```powershell
# Forcing a copy
$copy = $myHash.Clone()
```

## 3. Explicit Path (7+ Ref Keyword)
```powershell
# Pwsh supports [ref] for .NET method calls
[int]$i = 10
[Int32]::TryParse("20", [ref]$i)
```

# The Logic Bridge
// Logic: PowerShell passes objects by reference by default, but it masks this for simple primitives by creating clones during assignment.
