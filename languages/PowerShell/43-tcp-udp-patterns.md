# Template: TCP & UDP Patterns [SYSTEMS]

**Goal:** To define reliable vs. unreliable network streams.

---

## 1. Pwsh 5.1 / 7+ (TCP Stream)
```powershell
$client = [System.Net.Sockets.TcpClient]::new("127.0.0.1", 8080)
$stream = $client.GetStream()
$writer = [System.IO.StreamWriter]::new($stream)
$writer.WriteLine("Hello")
$writer.Flush()
```

## 2. Portable Path (UDP Send)
```powershell
$udp = [System.Net.Sockets.UdpClient]::new()
$data = [System.Text.Encoding]::UTF8.GetBytes("Ping")
$udp.Send($data, $data.Length, "127.0.0.1", 8080)
```

## 3. Explicit Path
```powershell
# Using a Listener
$listener = [System.Net.Sockets.TcpListener]::new([System.Net.IPAddress]::Any, 8080)
$listener.Start()
```

# The Logic Bridge
// Logic: TCP requires a stream writer/reader wrapper; UDP sends discrete byte-array packets.
