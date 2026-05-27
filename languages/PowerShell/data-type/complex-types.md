# Template: Complex & System Types [CORE]

**Goal:** To define advanced .NET type accelerators like `[xml]`, `[regex]`, and `[ipaddress]`.

---

## 1. Pwsh 5.1 / 7+ (Common)
```powershell
$xml = [xml]"<root><node>val</node></root>"
$ip = [ipaddress]"192.168.1.1"
```

## 2. Portable Path
```powershell
# Regex testing
$regex = [regex]"\d+"
$regex.IsMatch("123")
```

## 3. Explicit Path
```powershell
[guid]$id = [guid]::NewGuid()
[version]$ver = "1.2.3.4"
[uri]$url = "https://google.com"
[regex]$pattern = ".*"
```

# The Logic Bridge
// Logic: These accelerators map to specialized .NET classes (`System.Xml.XmlDocument`, `System.Net.IPAddress`, etc.) that handle validation and parsing automatically during assignment.
