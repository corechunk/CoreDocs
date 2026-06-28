# ⚙️ System Services & Privileged Userspace

Operating systems execute essential coordination systems in userspace (Ring 3) to protect the kernel from crashes while keeping system services isolated.

---

### 🧠 The Userspace Boot Handover: PID 1

At the end of kernel boot, the kernel exits Ring 0, drops CPU privilege registers to Ring 3, and spawns the first user space process: **PID 1 (Init)**.

```text
               +--------------------------------------+
               |      Kernel Finish Init (Ring 0)     |
               +--------------------------------------+
                                  |
                   [ Drops Privilege to Ring 3 ]
                                  |
                                  v
               +--------------------------------------+
               |      Spawns PID 1 (Init Binary)      |
               +--------------------------------------+
                /                 |                  \
       [ systemd (Linux) ]   [ launchd (macOS) ]  [ smss.exe (Windows) ]
```

Once PID 1 starts, it is responsible for spawning all other system daemons (linkers, logging, device managers, display servers) and user shell environments.

---

### 🗺️ Redirection Directory

*   📄 [**`system-initialization-init.md`**](./system-initialization-init.md) — Unix Init implementations: SysV Init scripts, systemd configurations, and BusyBox minimal setups.
*   📄 [**`windows-internals-registry.md`**](./windows-internals-registry.md) — Windows NT internals: Central Object Manager, Handles vs. Files, and the Registry configuration database.
*   📄 [**`macos-xnu-internals.md`**](./macos-xnu-internals.md) — macOS XNU hybrid kernel: Mach ports, IPC message passing, BSD layer wrappers, and launchd configurations.
