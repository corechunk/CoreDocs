# Template: TCP & UDP Patterns [SYSTEMS]

**Goal:** To distinguish between Stream-based (TCP) and Datagram-based (UDP) communication in Lua.

---

## 1. The Definition (Mental Model)
- **TCP:** A "Phone Call." Reliable, ordered, but slower (Handshakes).
- **UDP:** A "Letter." Fast, fire-and-forget, but unreliable (No delivery guarantee).

## 1. TCP Pattern (Reliable Stream)
```lua
local socket = require("socket")
local server = assert(socket.bind("*", 8080))
local client = server:accept()
local line = client:receive()
print(line)
```

## 2. UDP Pattern (Fast Datagram)
```lua
local socket = require("socket")

---@type table
local udp = assert(socket.udp())

-- Fire-and-forget to localhost
udp:sendto("Ping", "127.0.0.1", 8080)

print("Sent") -- Output: Sent
```

# The Logic Bridge
// Logic: TCP maintains a persistent stateful connection, while UDP is stateless and simply wraps data in an IP packet and ships it.
