# 🪟 Windows Named Pipes Implementation

Windows named pipes are managed by the NPFS subsystem and support multi-client, bidirectional, and message-oriented communication.

---

### 💻 Win32 Named Pipe Client-Server in C

#### Server Program (Creates Named Pipe)

```c
#include <windows.h>
#include <stdio.h>

#define PIPE_PATH L"\\\\.\\pipe\\MyWinPipe"
#define BUF_SIZE 512

int main() {
    // Create the named pipe in message mode
    HANDLE hPipe = CreateNamedPipeW(
        PIPE_PATH,
        PIPE_ACCESS_DUPLEX,      // Bidirectional access
        PIPE_TYPE_MESSAGE |      // Message-type pipe
        PIPE_READMODE_MESSAGE |  // Message-read mode
        PIPE_WAIT,               // Blocking mode
        1,                       // Max instances (1)
        BUF_SIZE,                // Output buffer size
        BUF_SIZE,                // Input buffer size
        0,                       // Client timeout (default)
        NULL                     // Default security
    );

    if (hPipe == INVALID_HANDLE_VALUE) {
        printf("CreateNamedPipe failed (%d)\n", GetLastError());
        return 1;
    }

    printf("Server: Waiting for client connection...\n");
    // Wait for client to connect
    if (ConnectNamedPipe(hPipe, NULL) ? TRUE : (GetLastError() == ERROR_PIPE_CONNECTED)) {
        printf("Server: Client connected.\n");

        char buffer[BUF_SIZE];
        DWORD bytesRead;
        
        // Read client message
        if (ReadFile(hPipe, buffer, BUF_SIZE - 1, &bytesRead, NULL)) {
            buffer[bytesRead] = '\0';
            printf("Received message: %s\n", buffer);
            
            // Send response back
            DWORD bytesWritten;
            WriteFile(hPipe, "ACK from Win32 Server", 21, &bytesWritten, NULL);
        }
    }

    DisconnectNamedPipe(hPipe);
    CloseHandle(hPipe);
    return 0;
}
```

#### Client Program (Connects to Named Pipe)

```c
#include <windows.h>
#include <stdio.h>

#define PIPE_PATH L"\\\\.\\pipe\\MyWinPipe"
#define BUF_SIZE 512

int main() {
    // Open named pipe as a standard file
    HANDLE hPipe = CreateFileW(
        PIPE_PATH,
        GENERIC_READ | GENERIC_WRITE,
        0, NULL, OPEN_EXISTING, 0, NULL
    );

    if (hPipe == INVALID_HANDLE_VALUE) {
        printf("Failed to open pipe. Server not running? (%d)\n", GetLastError());
        return 1;
    }

    // Set read mode of pipe to message mode
    DWORD dwMode = PIPE_READMODE_MESSAGE;
    SetNamedPipeHandleState(hPipe, &dwMode, NULL, NULL);

    // Write message
    DWORD bytesWritten;
    WriteFile(hPipe, "Hello Win32 Named Pipe Server!", 30, &bytesWritten, NULL);

    // Read response
    char buffer[BUF_SIZE];
    DWORD bytesRead;
    if (ReadFile(hPipe, buffer, BUF_SIZE - 1, &bytesRead, NULL)) {
        buffer[bytesRead] = '\0';
        printf("Server response: %s\n", buffer);
    }

    CloseHandle(hPipe);
    return 0;
}
```
