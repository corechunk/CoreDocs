# Encapsulation (PRO)

Definition: Restricting access to object members and bundling data with methods. In PowerShell, this is achieved using `hidden` and `private` keywords in classes (v5+).

## 1. Pwsh 5.1 (Legacy)
Using closure-based encapsulation (since classes were new).

```powershell
function New-User($name) {
    return @{
        GetName = { $name }
    }
}
```

## 2. Pwsh 7+ (Modern)
Using the `hidden` keyword in classes.

```powershell
class User {
    hidden [string]$Name
    User([string]$name) { $this.Name = $name }
    [string]GetName() { return $this.Name }
}
```

## 3. Portable Path
Standard class properties.

```powershell
class Data { [int]$Value }
```

## 4. Explicit Path
Explicit access via .NET reflection (System View).

```powershell
$u = [User]::new("Core")
$u.GetType().GetField("Name", "NonPublic,Instance")
```

# The Logic Bridge
// Logic: `hidden` members are still accessible via reflection but are filtered out of standard discovery tools like `Get-Member` and Tab-completion.
