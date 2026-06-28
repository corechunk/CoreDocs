# 🔌 POSIX Socket Allocation & File Descriptors

This manual details C socket programming, treating network sockets as standard Linux file descriptors (`int fd`).

---

## 1. Sockets as Linux File Descriptors

In Linux ("Everything is a File"), allocating a network socket returns a standard integer file descriptor indexing into the process's open file descriptor table. Sockets support standard system calls like `read()`, `write()`, and `close()`.

---

## 2. Server Socket Execution Loop Workflow

```text
[ socket() ] ──> [ bind() ] ──> [ listen() ] ──> [ accept() ] ──> [ read()/write() ]
```

1. **`int server_fd = socket(AF_INET, SOCK_STREAM, 0)`:** Requests kernel allocate an IPv4 TCP socket descriptor.
2. **`bind(server_fd, &addr, sizeof(addr))`:** Binds socket descriptor to local IP address and port number.
3. **`listen(server_fd, backlog)`:** Transitions socket into passive listening state with incoming connection queue.
4. **`int client_fd = accept(server_fd, &client_addr, &len)`:** Blocks until a client connects, returning a brand new file descriptor dedicated exclusively to client communication.
