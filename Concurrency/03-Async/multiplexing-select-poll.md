# 🔀 OS Event Multiplexing (select, poll, epoll)

Operating systems provide interfaces to monitor multiple file descriptors (sockets, pipes) for changes, notifying userspace only when I/O operations can be run without blocking.

---

### 🧠 Performance Scalability Comparison

*   **`select()`**: Uses static bitsets. It loops through all descriptors ($O(N)$ lookup) on every query. $1024$ FD limit.
*   **`poll()`**: Uses dynamic arrays of structs. Still requires linear traversal ($O(N)$ lookup). No FD limit.
*   **`epoll()`**: Linux-specific. Uses kernel-level ready lists (RB-Tree / list). Only active FDs are returned ($O(1)$ lookup).

---

### 💻 Epoll implementation in C

```c
#include <stdio.h>
#include <sys/epoll.h>
#include <unistd.h>

#define MAX_EVENTS 5

int main() {
    int epoll_fd = epoll_create1(0);
    struct epoll_event event, events[MAX_EVENTS];

    // Monitor stdin (FD 0) for input events
    event.events = EPOLLIN;
    event.data.fd = 0;
    epoll_ctl(epoll_fd, EPOLL_CTL_ADD, 0, &event);

    printf("Monitoring stdin via epoll...\n");
    int num_fds = epoll_wait(epoll_fd, events, MAX_EVENTS, -1); // Block until event occurs

    for (int i = 0; i < num_fds; i++) {
        if (events[i].data.fd == 0) {
            printf("Data is available to read on stdin!\n");
        }
    }

    close(epoll_fd);
    return 0;
}
```
