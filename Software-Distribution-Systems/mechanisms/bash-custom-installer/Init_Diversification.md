# Init System Diversification: Beyond Systemd

When building a "Universal Installer," you cannot assume the system uses Systemd. To ensure your background processes (Daemons) run on specialized distros like Alpine (OpenRC), Void (Runit), or Devuan (SysVinit), your installer must implement an **Init Detection & Deployment Matrix**.

---

## 🔍 Detection Logic: Which Init is Running?

Your installer script should use a conditional ladder to detect the active init system before deploying service files.

```bash
if [ -d "/run/systemd/system" ]; then
    INIT_SYSTEM="systemd"
elif [ -x "/sbin/openrc-run" ]; then
    INIT_SYSTEM="openrc"
elif [ -d "/etc/sv" ] && [ -x "/usr/bin/runit" ]; then
    INIT_SYSTEM="runit"
elif [ -d "/etc/init.d" ]; then
    INIT_SYSTEM="sysvinit"
else
    INIT_SYSTEM="unknown"
fi
```

---

## 🛠️ Deployment Blueprints

### 1. Systemd (The Modern Standard)
*   **Path:** `/etc/systemd/system/` (Local) or `/usr/lib/systemd/system/` (Packages).
*   **Mechanism:** Declarative `.service` file.
*   **Blueprint:**
    ```ini
    [Unit]
    Description=My Application Daemon
    After=network.target

    [Service]
    Type=simple
    ExecStart=/usr/local/bin/my-app-daemon
    Restart=on-failure

    [Install]
    WantedBy=multi-user.target
    ```

### 2. OpenRC (Alpine, Gentoo, Artix)
*   **Path:** `/etc/init.d/`
*   **Mechanism:** Shell script with the `#!/sbin/openrc-run` shebang.
*   **Blueprint:**
    ```bash
    #!/sbin/openrc-run
    description="My Application Daemon"
    command="/usr/local/bin/my-app-daemon"
    command_background="true"
    pidfile="/run/${RC_SVCNAME}.pid"

    depend() {
        need net
        after bootmisc
    }
    ```

### 3. SysVinit (Legacy & Minimalist)
*   **Path:** `/etc/init.d/`
*   **Mechanism:** Standard shell script handling `start|stop|restart` cases.
*   **Blueprint:**
    ```bash
    #!/bin/sh
    case "$1" in
        start)
            echo "Starting my-app..."
            start-stop-daemon --start --background --exec /usr/local/bin/my-app-daemon
            ;;
        stop)
            echo "Stopping my-app..."
            start-stop-daemon --stop --exec /usr/local/bin/my-app-daemon
            ;;
        *)
            echo "Usage: $0 {start|stop}"
            exit 1
            ;;
    esac
    ```

### 4. Runit (Void Linux, AntiX)
*   **Path:** `/etc/sv/my-app/`
*   **Mechanism:** A directory containing an executable `run` file.
*   **Blueprint:**
    ```bash
    #!/bin/sh
    exec /usr/local/bin/my-app-daemon 2>&1
    ```
    *Note: To enable, the user or installer must symlink this directory to `/var/service/`.*

---

## ⚖️ Comparative Strategy

| Init System | Style | Difficulty to Target | Popularity |
| :--- | :--- | :--- | :--- |
| **Systemd** | Unit-based | Low | Very High (Debian, Fedora, Arch) |
| **OpenRC** | Script-based | Moderate | High (Alpine, Gentoo) |
| **SysVinit** | Procedural | High | Moderate (Devuan, MX Linux) |
| **Runit** | Directory-based | Low | Low (Void) |

**Pro-Tip:** Always provide a Systemd unit by default, but include an `init/` folder in your source tree with these templates for advanced users.
