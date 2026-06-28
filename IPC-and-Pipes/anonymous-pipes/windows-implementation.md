# 🪟 Windows Anonymous Pipes Implementation

In the Windows subsystem (Win32), anonymous pipes are created via `CreatePipe()` and redirected into child processes using handle inheritance and `STARTUPINFO` configurations.

---

### 🧠 Handle Table & Inheritance Mechanics

Unlike UNIX file descriptors, Windows handles are objects managed in a process-specific handle table. By default, handles are **not inherited** by child processes.
1.  We must explicitly configure `SECURITY_ATTRIBUTES` to set `bInheritHandle = TRUE`.
2.  During child process creation via `CreateProcessW()`, we must pass `bInheritHandles = TRUE`.
3.  We map the pipe handles to the child's standard streams using `STARTUPINFO` attributes.

---

### 💻 Win32 Pipeline Implementation in C

This program spawns a child process running `cmd.exe /c dir` and reads its output through an anonymous pipe.

```c
#include <windows.h>
#include <stdio.h>

#define BUFSIZE 4096

int main() {
    HANDLE hChildStd_OUT_Rd = NULL;
    HANDLE hChildStd_OUT_Wr = NULL;
    SECURITY_ATTRIBUTES saAttr;

    // Set handle inheritance properties
    saAttr.nLength = sizeof(SECURITY_ATTRIBUTES);
    saAttr.bInheritHandle = TRUE; // Child will inherit this handle
    saAttr.lpSecurityDescriptor = NULL;

    // Create the anonymous pipe
    if (!CreatePipe(&hChildStd_OUT_Rd, &hChildStd_OUT_Wr, &saAttr, 0)) {
        printf("CreatePipe failed (%d)\n", GetLastError());
        return 1;
    }

    // Ensure the read handle is not inherited by the child
    if (!SetHandleInformation(hChildStd_OUT_Rd, HANDLE_FLAG_INHERIT, 0)) {
        printf("SetHandleInformation failed (%d)\n", GetLastError());
        return 1;
    }

    // Create the child process
    PROCESS_INFORMATION piProcInfo;
    STARTUPINFOW siStartInfo;
    ZeroMemory(&piProcInfo, sizeof(PROCESS_INFORMATION));
    ZeroMemory(&siStartInfo, sizeof(STARTUPINFOW));

    siStartInfo.cb = sizeof(STARTUPINFOW);
    siStartInfo.hStdError = hChildStd_OUT_Wr;  // Bind write end to child stderr
    siStartInfo.hStdOutput = hChildStd_OUT_Wr; // Bind write end to child stdout
    siStartInfo.dwFlags |= STARTF_USESTDHANDLES;

    wchar_t cmdLine[] = L"cmd.exe /c dir";

    // Spawn child
    BOOL bSuccess = CreateProcessW(
        NULL, 
        cmdLine, 
        NULL, 
        NULL, 
        TRUE, // Parent handles marked as inheritable are duplicated to child
        0, 
        NULL, 
        NULL, 
        &siStartInfo, 
        &piProcInfo
    );

    if (!bSuccess) {
        printf("CreateProcess failed (%d)\n", GetLastError());
        return 1;
    }

    // Close the write end of the pipe in the parent so it detects EOF
    CloseHandle(hChildStd_OUT_Wr);

    // Read execution output from the pipe
    DWORD dwRead;
    CHAR chBuf[BUFSIZE];
    while (ReadFile(hChildStd_OUT_Rd, chBuf, BUFSIZE - 1, &dwRead, NULL) && dwRead > 0) {
        chBuf[dwRead] = '\0';
        printf("%s", chBuf);
    }

    // Cleanup process resources
    CloseHandle(piProcInfo.hProcess);
    CloseHandle(piProcInfo.hThread);
    CloseHandle(hChildStd_OUT_Rd);

    return 0;
}
```
