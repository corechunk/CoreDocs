# 🔴 Milestone 42: Socket Basics [SYSTEMS]

### 1. Network Streams
Bash can open raw network connections without external tools like `curl`. It uses a virtual path system to map TCP/UDP addresses to standard shell file descriptors.

```bash
# EXPLICIT: Opening a Raw TCP Stream
# Syntax: /dev/tcp/HOST/PORT
exec 3<>/dev/tcp/google.com/80 # Logic: Assign stream to FD 3

# Logic: /dev/tcp is an internal Bash interceptor. It triggers 
# the socket() and connect() system calls during the redirection 
# phase.
```

### 2. Socket Communication
Once a descriptor is bound to a network stream, you can use standard shell built-ins (`echo`, `read`) to interact with the remote server.

```bash
# EXPLICIT: HTTP Request
echo -e "GET / HTTP/1.1\r\nHost: google.com\r\n\r\n" >&3
head -n 1 <&3               # Logic: Read first line of response

# CLEANUP
exec 3>&-                   # Close the descriptor
```
