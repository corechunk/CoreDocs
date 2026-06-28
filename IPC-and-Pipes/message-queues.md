# 📧 POSIX Message Queues

POSIX message queues allow related or unrelated processes to exchange data in the form of discrete, prioritized messages (`mqueue.h`). Unlike stream-oriented pipes, message queues preserve boundaries and allow prioritizing urgent messages.

---

### 🧠 Core Mechanics

*   **Message Boundaries**: Each read operation retrieves exactly one message written by a write operation (no fragmentation or merging of streams).
*   **Prioritization**: Each message is sent with an integer priority value. Messages are stored and retrieved in priority order (highest priority first), rather than strict FIFO order.

---

### 💻 POSIX Message Queue in C

#### Server Program (Receives Messages)

```c
#include <stdio.h>
#include <stdlib.h>
#include <fcntl.h>
#include <sys/stat.h>
#include <mqueue.h>

#define QUEUE_NAME "/sys_msg_queue"
#define MAX_SIZE 1024

int main() {
    struct mq_attr attr;
    attr.mq_flags = 0;
    attr.mq_maxmsg = 10;
    attr.mq_msgsize = MAX_SIZE;
    attr.mq_curmsgs = 0;

    // Open/Create the queue
    mqd_t mq = mq_open(QUEUE_NAME, O_CREAT | O_RDONLY, 0644, &attr);
    if (mq == (mqd_t)-1) {
        perror("mq_open failed");
        return 1;
    }

    char buffer[MAX_SIZE];
    unsigned int priority;
    
    printf("Server: Waiting for messages...\n");
    // Retrieve highest priority message
    ssize_t bytes_read = mq_receive(mq, buffer, MAX_SIZE, &priority);
    if (bytes_read >= 0) {
        buffer[bytes_read] = '\0';
        printf("Received (Priority %u): %s\n", priority, buffer);
    }

    mq_close(mq);
    mq_unlink(QUEUE_NAME);
    return 0;
}
```

#### Client Program (Sends Messages)

```c
#include <stdio.h>
#include <fcntl.h>
#include <mqueue.h>

#define QUEUE_NAME "/sys_msg_queue"

int main() {
    mqd_t mq = mq_open(QUEUE_NAME, O_WRONLY);
    if (mq == (mqd_t)-1) {
        perror("Failed to open queue");
        return 1;
    }

    char msg[] = "High priority message payload!";
    unsigned int priority = 10; // Numeric priority level
    
    printf("Client: Sending message with priority %u...\n", priority);
    mq_send(mq, msg, sizeof(msg), priority);

    mq_close(mq);
    return 0;
}
```
