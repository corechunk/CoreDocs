# Core Extraction Logic: Self-Extracting Archive

The self-extracting archive (SFX) is the most powerful "distro-neutral" pattern for custom installers. It combines a human-readable Bash script with an embedded binary payload.

## 🏗️ The SFX Architecture

```text
+------------------------------------------------------+
| Part 1: Installation Logic (Bash Script)             |
| - Parse parameters (--prefix, --user, --uninstall)   |
| - Verify system dependencies (tar, gzip, sudo)       |
| - Detect Init System (Systemd vs OpenRC)             |
| - Extract embedded binary payload                    |
+------------------------------------------------------+
| Boundary Identifier Marker: __ARCHIVE_FOLLOWS__      |
+------------------------------------------------------+
| Part 2: Compressed Application Payload (.tar.gz)     |
| - Binary data (garbage-looking text)                 |
+------------------------------------------------------+
```

## 📜 Production-Grade Installer Template

```bash
#!/bin/sh
set -eu

APP_NAME="linutils"
MANIFEST_DIR="/var/log/${APP_NAME}"

# 1. Path Setup & Argument Parsing
PREFIX="/usr/local"
for arg in "$@"; do
    case $arg in
        --user) PREFIX="${HOME}/.local"; MANIFEST_DIR="${HOME}/.local/share/${APP_NAME}";;
        --uninstall) UNINSTALL=true;;
    esac
done

# 2. Uninstallation Logic (Manifest-Based)
if [ "${UNINSTALL:-false}" = true ]; then
    MANIFEST="${MANIFEST_DIR}/install.receipt"
    while read -r item; do
        [ -f "$item" ] || [ -L "$item" ] && rm -f "$item"
        [ -d "$item" ] && rmdir "$item" 2>/dev/null || true
    done < "$MANIFEST"
    rm -f "$MANIFEST"
    exit 0
fi

# 3. Extraction Logic
# Locate the line number where the payload starts
ARCHIVE_LINE=$(awk '/^__ARCHIVE_FOLLOWS__/ {print NR + 1; exit 0;}' "$0")

# Extract to temp directory
TMP_DIR=$(mktemp -d)
tail -n +"${ARCHIVE_LINE}" "$0" | tar -xzf - -C "${TMP_DIR}"

# 4. Deployment & Tracking
mkdir -p "${PREFIX}/bin" "${MANIFEST_DIR}"
MANIFEST="${MANIFEST_DIR}/install.receipt"
true > "$MANIFEST"

# Deploy binary
cp "${TMP_DIR}/bin/app" "${PREFIX}/bin/${APP_NAME}"
echo "${PREFIX}/bin/${APP_NAME}" >> "$MANIFEST"

# Clean up
rm -rf "${TMP_DIR}"
exit 0

__ARCHIVE_FOLLOWS__
```

## 🔨 How to Build the Final Installer

Once you have your `installer.sh` and your application folder `dist/`, run these steps:

1.  **Compress the payload:**
    ```bash
    tar -czf payload.tar.gz -C dist/ .
    ```
2.  **Concatenate into a single ".run" file:**
    ```bash
    cat installer.sh payload.tar.gz > install_linutils.run
    chmod +x install_linutils.run
    ```

## 🧪 Advanced Considerations
*   **Shebang:** Use `#!/bin/sh` for maximum portability (runs on Dash, Bash, Zsh, and busybox).
*   **Write Tests:** Always check if the prefix is writeable before starting extraction:
    ```bash
    if [ ! -w "$PREFIX" ]; then echo "Error: No write access to $PREFIX"; exit 1; fi
    ```
