# Template: Socket Basics [SYSTEMS]

**Goal:** To define low-level TCP/UDP communication using .NET Sockets.

---

## 1. Pwsh 5.1 (Legacy .NET)
```powershell
$socket = New-Object System.Net.Sockets.TcpClient("127.0.0.1", 80)
```

## 2. Pwsh 7+ (Modern Generic)
```powershell
$socket = [System.Net.Sockets.TcpClient]::new("127.0.0.1", 80)
```

## 3. Portable Path
```powershell
# Testing a port
Test-NetConnection -ComputerName "127.0.0.1" -Port 80
```

## 4. Explicit Path
```powershell
[System.Net.Sockets.Socket]$raw = [System.Net.Sockets.Socket]::new(
    [System.Net.Sockets.AddressFamily]::InterNetwork,
    [System.Net.Sockets.SocketType]::Stream,
    [System.Net.Sockets.ProtocolType]::Tcp
)
```

# The Logic Bridge
// Logic: PowerShell abstracts raw sockets into the `TcpClient` class for easier stream handling.
