# 🪟 Windows NT Internals & The Registry

The Windows NT operating system architecture departs from UNIX design patterns, using an object-oriented kernel architecture and a centralized configuration database.

---

### 1. The NT Object Manager & Handles

Windows NT does not use raw integer file descriptors. Instead, the **Object Manager** (a subsystem inside the NT Executive) manages all kernel-level resources (Processes, Threads, Files, Mutexes, Events) as unified **Objects**.
*   **Handles**: Userspace applications manipulate these resources using virtual indices called **Handles**.
*   **Unified Access**: You can wait for a Thread to terminate, a File to complete read, or a Mutex to unlock using the identical system API: `WaitForSingleObject(HANDLE, ...)`.

---

### 2. The Registry System Database

Unlike UNIX systems which store system configurations in plain-text files across directories (e.g. `/etc/`), Windows stores configurations in a hierarchical binary database called the **Registry**.
*   **Hives**: The Registry is split into logical files called **Hives** (e.g. `SYSTEM`, `SOFTWARE`, `SECURITY`) loaded directly into kernel memory during early boot.
*   **Keys and Values**: Structured like a directory tree containing keys (folders) and values (files containing strings, integers, or binary blobs).

---

### 3. Subsystem Servers (Win32 & POSIX)

The Windows NT kernel does not directly expose the Win32 API. Instead, it exposes a low-level native API (`ntdll.dll`).
*   **Subsystems**: Windows runs userspace Subsystem Servers (like `csrss.exe` - Client Server Runtime Subsystem) to translate Win32 calls into native NT system calls.
*   **POSIX Subsystem**: Historically, Windows NT supported running a POSIX subsystem alongside Win32, allowing standard UNIX compiles to run natively on the NT kernel without emulation.
