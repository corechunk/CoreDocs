# State Machine Hooks (.install)

While Debian uses separate files (`postinst`, `prerm`), Arch Linux consolidates lifecycle hooks into a single companion file, usually named `pkgname.install`.

## ⚙️ How it works
You register the install file in your `PKGBUILD` using: `install=linutils.install`.

Inside the `.install` file, you define specific shell functions that Pacman calls at precise moments:

```bash
# 1. After extraction
post_install() {
    echo "Updating desktop database..."
    update-desktop-database -q
}

# 2. After an upgrade
# $1: New version, $2: Old version
post_upgrade() {
    if [ "$(vercmp "$2" "2.0.0")" -lt 0 ]; then
        echo "WARNING: Config path changed to ~/.config/linutils/"
    fi
}

# 3. Before removal
pre_remove() {
    systemctl stop linutils-worker.service
}
```

---

## 🏗️ Pacman Database State (`/var/lib/pacman/local/`)

Every installed package has its own directory here. It contains:
*   **`desc`:** The package metadata (Name, Version, **Install Reason**).
*   **`files`:** An absolute tracking index of every file the package dropped on the system.

### The Install Reason Flag (`%REASON%`)
*   **`0`:** Explicitly installed by the user (`pacman -S`).
*   **`1`:** Automatically installed as a dependency.

**Why this matters:** When a user runs `pacman -Rs app`, Pacman checks this flag. It will only auto-remove dependencies that have a `%REASON%` of `1` AND have no other parent packages linking to them.
