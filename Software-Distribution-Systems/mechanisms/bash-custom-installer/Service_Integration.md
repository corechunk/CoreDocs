# Service & Init Integration

A truly universal installer must detect the host's initialization system to properly deploy background daemons or workers.

## 🔍 Detection Logic

In your installer script, use these checks to determine the target environment:

```bash
if [ -d "/run/systemd/system" ]; then
    INIT_TYPE="systemd"
elif [ -x "/sbin/openrc-run" ]; then
    INIT_TYPE="openrc"
elif [ -d "/etc/init.d" ]; then
    INIT_TYPE="sysvinit"
elif [ -d "/etc/sv" ]; then
    INIT_TYPE="runit"
else
    INIT_TYPE="unknown"
fi
```

---

## ⚙️ Target Templates

### 1. Systemd (Standard)
*   **Path:** `/etc/systemd/system/` (Local) or `/usr/lib/systemd/system/` (Packages).
*   **Unit File:**
    ```ini
    [Unit]
    Description=My App Daemon
    After=network.target

    [Service]
    ExecStart=/usr/local/bin/my-app
    Restart=always

    [Install]
    WantedBy=multi-user.target
    ```

### 2. OpenRC (Alpine, Gentoo, Artix)
*   **Path:** `/etc/init.d/`
*   **Runscript:**
    ```bash
    #!/sbin/openrc-run
    command="/usr/local/bin/my-app"
    command_background="true"
    pidfile="/run/${RC_SVCNAME}.pid"
    ```

### 3. SysVinit (Legacy/Minimal)
*   **Path:** `/etc/init.d/`
*   **Script:** Requires a `case` statement for `start|stop|restart` using `start-stop-daemon`.

---

## 🛠️ Deployment Workflow

When your installer extracts the payload, it should check `INIT_TYPE` and copy the appropriate service file:

```bash
case $INIT_TYPE in
    systemd)
        cp "${TMP_DIR}/init/app.service" "/etc/systemd/system/"
        systemctl daemon-reload
        ;;
    openrc)
        cp "${TMP_DIR}/init/app.init" "/etc/init.d/app"
        chmod +x "/etc/init.d/app"
        ;;
esac
```

## ⚠️ The Immutable OS Exception
On **Atomic/Immutable distributions** (Fedora Silverblue, SteamOS), `/usr/` is read-only.
*   **Detection:** `if [ ! -w "/usr/local/bin" ] && [ -d "/var/usrlocal" ]; then ...`
*   **Fix:** Adjust your `PREFIX` to `/var/usrlocal/bin` if the immutable path is detected.
