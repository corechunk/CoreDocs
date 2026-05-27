# 🏛️ Master Pwsh Reference (One-Shot)

**Target Standard:** Hybrid (Pwsh 5.1 & Pwsh 7.4)
**Pedagogical Model:** Quad-Snippet Hybrid (5.1 vs 7+ vs Portable vs Explicit)

---

## 🟢 Tier 1: The Foundation [CORE]

### 01. Keywords Master List
Keywords are the hard-coded grammar of PowerShell. 

| Category | Keywords |
| :--- | :--- |
| **Control** | `if`, `else`, `switch`, `foreach`, `for`, `while`, `do`, `until`, `break`, `continue`, `return`, `exit` |
| **Error** | `try`, `catch`, `finally`, `throw`, `trap` |
| **Blocks** | `function`, `filter`, `begin`, `process`, `end`, `clean`, `param`, `dynamicparam` |
| **OOP** | `class`, `enum`, `interface`, `using`, `hidden`, `static`, `base` |

#### 1. Modern Syntax Comparison
```powershell
# Legacy (5.1)
if ($a -eq $null) { $b = 1 } else { $b = $a }

# Modern (7.0+)
$b = $a ?? 1
```

---

### 02. Data Types (Type Accelerators)
Everything is a .NET Object. Shorthand `[type]` names are called Type Accelerators.

| Accelerator | .NET Type |
| :--- | :--- |
| `[object]` | `System.Object` (Base) |
| `[int]` | `System.Int32` |
| `[long]` | `System.Int64` |
| `[decimal]` | `System.Decimal` |
| `[char]` | `System.Char` |
| `[xml]` | `System.Xml.XmlDocument` |
| `[ipaddress]` | `System.Net.IPAddress` |

#### 1. Explicit Path Snippet
```powershell
[object]$any = 123
[Int32]$id = 1
[DateTime]$now = Get-Date
[System.Net.IPAddress]$ip = "127.0.0.1"
[pscustomobject]$user = @{ Name = "Admin" }
```

# The Logic Bridge
// Logic: PowerShell variables are objects; typing them restricts the underlying .NET type assigned to the variable name.
