# 🏁 System Initialization (Init Systems)

The `init` process is the first process started during boot (PID 1) and serves as the parent of all userspace processes. Different Unix-like systems implement this using differing paradigms.

---

### 🧠 Three Common Unix Init Configurations

1.  **SysV Init (System V - Classical)**:
    *   Uses shell scripts located in `/etc/init.d/` mapped to numerical **Runlevels** (e.g. Runlevel 3 for CLI, Runlevel 5 for GUI).
    *   *Drawback*: Services start sequentially, resulting in slower boot times.
2.  **systemd (Modern standard)**:
    *   Organizes boot components into declarative configuration files called **Units** (e.g., `.service`, `.target`).
    *   Spawns services in parallel using socket activation (the init system creates sockets immediately, allowing dependent programs to boot simultaneously).
3.  **BusyBox Init (Embedded)**:
    *   A single minimal binary providing a lightweight `init` replacement for embedded Linux and Termux environments. Configured via simple `/etc/inittab` files.

---

### 💻 systemd Unit Configuration Example

A minimal declarative unit file (`/etc/systemd/system/myapp.service`) to manage a custom backend service:

```ini
[Unit]
Description=My Custom Backend Service
After=network.target # Start after network driver is initialized

[Service]
Type=simple
ExecStart=/usr/bin/myapp --port 8080
Restart=on-failure # Automatically restart if process exits with error

[Install]
WantedBy=multi-user.target # Equal to Runlevel 3 (multi-user console environment)
```
