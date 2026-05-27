# 🔴 Milestone 43: TCP/UDP Patterns [SYSTEMS]

### 1. Reliable Streams (TCP)
TCP is a connection-oriented protocol that ensures every byte arrives in order. In Bash, this is used for reliable data transfers or simple HTTP interaction.

```bash
# EXPLICIT: TCP Send & Receive
{
    echo "MSG" >&3          # Write
    read -r resp <&3        # Read
} 3<>/dev/tcp/localhost/1234

# Logic: TCP uses a 3-way handshake to establish a persistent 
# virtual circuit in the Kernel's network stack.
```

### 2. Fast Datagrams (UDP)
UDP is a "Fire and Forget" protocol. It is faster than TCP but does not guarantee delivery. In Bash, this is ideal for high-speed logging or DNS queries.

```bash
# EXPLICIT: UDP Fire-and-Forget
echo "<14>System Alert" >/dev/udp/syslog.local/514

# Logic: UDP creates a socket (SOCK_DGRAM) and sends a packet 
# directly to the destination IP without waiting for an 
# acknowledgment.
```
