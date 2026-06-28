# ⚡ Linux io_uring

`io_uring` is a high-performance Linux kernel interface designed to perform asynchronous system calls via lock-less ring buffers, removing user-to-kernel context-switching overhead.

---

### 🧠 Ring Buffer Architecture

`io_uring` uses two circular ring buffers shared directly between userspace and kernel space:

1.  **Submission Queue (SQ)**: Userspace writes request entries (SQEs) containing target operations (`read`, `write`, `accept`).
2.  **Completion Queue (CQ)**: The kernel writes result entries (CQEs) showing status and byte transfer counts.

```text
  Userspace                     Shared Memory Memory-Mapped              Linux Kernel
+-----------+                   +--------------------------+             +------------+
| App writes| -- SQE write -->  |  Submission Queue (SQ)   | -- reads -> | Executes   |
| request   |                   +--------------------------+             | Syscall    |
+-----------+                   +--------------------------+             | Async      |
| App reads | <-- CQE read ---  |   Completion Queue (CQ)  | <- writes - +------------+
| completion|                   +--------------------------+
+-----------+
```

---

### 💻 Basic io_uring Setup in C

```c
#include <stdio.h>
#include <liburing.h>
#include <unistd.h>
#include <fcntl.h>

int main() {
    struct io_uring ring;
    // Initialize ring with 8 queue depth slots
    if (io_uring_queue_init(8, &ring, 0) < 0) {
        perror("Failed to init io_uring");
        return 1;
    }

    struct io_uring_sqe *sqe = io_uring_get_sqe(&ring);
    if (!sqe) return 1;

    // Prep an asynchronous NOP request
    io_uring_prep_nop(sqe);
    
    // Submit request to kernel and wait for completion
    io_uring_submit_and_wait(&ring, 1);

    struct io_uring_cqe *cqe;
    io_uring_peek_cqe(&ring, &cqe);
    if (cqe->res >= 0) {
        printf("io_uring asynchronous NOP completed successfully.\n");
    }

    io_uring_cqe_seen(&ring, cqe);
    io_uring_queue_exit(&ring);
    return 0;
}
```
