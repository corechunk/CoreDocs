# 34 - Structs Base (CORE - Hub)

Definition: PowerShell uses `hashtables` and `PSCustomObject` as the gateway to Procedural-style data modeling. They allow you to group related variables into a single unit for efficient data passing.

## Deep-Dive Reference
For modular procedural architecture:
- [Procedural Mechanisms](./procedural/35-procedural-mechanisms.md)

---

## 1. Pwsh 5.1 (Legacy)
Using a Hashtable for simple grouping.

```powershell
$config = @{
    Port = 80
    Host = "localhost"
}
$config.Port = 8080 # Access via dot-operator
```

## 2. Pwsh 7+ (Modern)
Using `[PSCustomObject]` for a rigid data record.

```powershell
$config = [PSCustomObject]@{
    Port = 443
    Host = "127.0.0.1"
}
Write-Host "$($config.Host):$($config.Port)" # Output: 127.0.0.1:443
```

## 3. Portable Path
Creating records from CSV or JSON (Zero-dependency).

```powershell
$data = '{"id": 1}' | ConvertFrom-Json
$data.id # Output: 1
```

## 4. Explicit Path
Defining a struct-like class for strict typing.

```powershell
class DataBag {
    [int]$Id
    [string]$Value
}
[DataBag]$d = [DataBag]@{ Id = 1; Value = "Txt" }
```

# The Logic Bridge
// Logic: A `PSCustomObject` is a .NET wrapper that allows for dynamic property access. Unlike a hashtable, it has a stable memory representation and supports the standard dot-operator as a first-class citizen in the pipeline.
