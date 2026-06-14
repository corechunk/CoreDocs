# Lifecycle Maintainer Scripts

Debian packages provide four distinct shell scripts (Hooks) to handle system logic during the software's lifecycle. These scripts execute with **root privileges**.

## 🔄 The Hook Cycle

| Script | When it runs | Primary Use-Case |
| :--- | :--- | :--- |
| **`preinst`** | Before unpacking | Stop services; Check system compatibility. |
| **`postinst`** | After unpacking | Compile schemas; Start services; Add system users. |
| **`prerm`** | Before removal | Stop active daemons; Warn the user. |
| **`postrm`** | After removal | Clean up logs; Purge configuration files. |

---

## 📜 Examples

### 1. Adding a System User (`postinst`)
```bash
#!/bin/sh
set -e
if [ "$1" = "configure" ]; then
    if ! getent passwd linutils > /dev/null; then
        adduser --system --group --no-create-home linutils
    fi
fi
```

### 2. Restarting Systemd (`postinst` / `postrm`)
```bash
#!/bin/sh
set -e
if [ -d /run/systemd/system ]; then
    systemctl daemon-reload
fi
```

---

## ⚠️ Critical Rule: Idempotency
Maintainer scripts MUST be **idempotent**. This means if you run the script twice, it should not fail or create duplicate entries.
*   **Bad:** `echo "config" >> /etc/main.conf` (Appends every time).
*   **Good:** `grep -q "config" /etc/main.conf || echo "config" >> /etc/main.conf` (Only appends if missing).

## 🛠️ Testing Environment
Always test your scripts in a clean container (Docker/Podman) before deploying to a physical machine, as a bug in a `postinst` script can leave a user's `apt` engine in a broken, "locked" state.
