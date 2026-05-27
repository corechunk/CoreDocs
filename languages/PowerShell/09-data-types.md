# Template: Data Types [CORE]

**Goal:** To define the .NET-backed type system in PowerShell and how the engine performs auto-coercion.

---

## 1. The Definition (Mental Model)
Every value in PowerShell is a .NET Object. The absolute base type for everything is **`[object]`** (`System.Object`). The engine automatically maps common primitives to their .NET equivalents, but they all inherit from the object root. PowerShell uses **Type Accelerators** (shorthand names in brackets) to make referencing these types easier.

- **Numbers:** [numbers.md](./data-type/numbers.md) (`[int]`, `[long]`, `[double]`, `[decimal]`, `[byte]`)
- **Strings & Characters:** [strings-chars.md](./data-type/strings-chars.md) (`[string]`, `[char]`)
- **Booleans:** [booleans.md](./data-type/booleans.md) (`[bool]`)
- **Nulls ($null):** [nil.md](./data-type/nil.md)
- **Dates & Times:** [dates-times.md](./data-type/dates-times.md) (`[datetime]`, `[timespan]`)
- **Complex & System:** [complex-types.md](./data-type/complex-types.md) (`[xml]`, `[regex]`, `[guid]`, `[ipaddress]`, `[uri]`)
- **Special types:** [special-types.md](./data-type/special-types.md) (`[pscustomobject]`, `[scriptblock]`, `[type]`)

## 1. Pwsh 5.1 / 7+ (Common)
```powershell
$obj = "Hello"
$obj.GetType().FullName
# Output: System.String
```

## 2. Portable Path
```powershell
# Type checking
if ($obj -is [string]) { "Is String" }
```

## 3. Explicit Path
```powershell
[Int32]$id = 1
[DateTime]$now = Get-Date
[System.Net.IPAddress]$ip = "127.0.0.1"
```

# The Logic Bridge
// Logic: PowerShell's "Type Adapters" allow it to treat heterogeneous .NET objects as unified data points in the pipeline; type accelerators act as aliases for the underlying .NET Class hierarchy.
