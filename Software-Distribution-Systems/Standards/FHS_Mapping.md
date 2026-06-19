# FHS: Binary Locations & Purposes

The Filesystem Hierarchy Standard (FHS) explicitly separates files based on who manages them (OS vs. Administrator) and who can access them (System vs. User).

## 🗺️ Path Distribution Map

| Binary Path | Scope | Managed By | Primary Purpose |
| :--- | :--- | :--- | :--- |
| **`/bin`** | System-Wide | Official Package Manager | Essential binaries for boot/repair (`ls`, `bash`). |
| **`/usr/bin`** | System-Wide | Official Package Manager | Primary location for user programs (`gcc`, `ffmpeg`). |
| **`/usr/local/bin`** | System-Wide | Host Administrator | Local software installed via **Installer Scripts**. |
| **`~/.local/bin`** | User-Specific | Single User | Personal utilities (No `sudo` required). |
| **`/opt/`** | System-Wide | Third-Party Vendor | Monolithic, self-contained app bundles (e.g., Chrome). |

---

## ⚖️ Distribution Targeting Logic

To prevent breaking system state, each distribution format must target a specific tier:

1.  **Native Packages (`.deb`, `.pkg`, `.rpm`):** MUST target **`/usr/bin`**. These are tracked by the OS database.
2.  **Root Installer Scripts:** MUST target **`/usr/local/bin`**. This signals "Manual/Admin Installation" to the OS.
3.  **User-Space Installers:** MUST target **`~/.local/bin`**. This is for zero-privilege deployment.
4.  **AppImage:** Operates from **`/tmp/`** via dynamic FUSE mounting; often stored in `~/Applications/` or `/opt/`.

---

## ⚡ The Shadowing Conflict

Linux shells search the `$PATH` environment variable from **left to right**. A typical path:
`~/.local/bin : /usr/local/bin : /usr/bin : /bin`

*   **Shadowing:** If you have `linutils` in both `/usr/local/bin` and `/usr/bin`, the shell will execute the one in `/usr/local/bin`.
*   **The Trap:** If you update the app via `apt` (to `/usr/bin`), you will still be running the **old version** in `/usr/local/bin` without realizing it.

**Rule of Thumb:** Never install the same app via both an Installer Script and a Package Manager simultaneously.

## 🚦 Path Precedence & Shadowing Hierarchy

The order of directories in the `$PATH` variable creates a hierarchy of execution. Understanding this is critical for preventing "Ghost Version" bugs.

### Precedence Tiers (Typical Linux)
1.  **OS Managed:** `/bin`, `/usr/bin` (Highest Priority)
2.  **Admin Managed:** `/usr/local/bin`
3.  **User Managed:** `~/.local/bin` (Lowest Priority)

### The Shadowing Rule
If `Precedence(ExistingPath) > Precedence(TargetPath)`, the new installation will be **shadowed**. The user will continue to run the old version unless they provide the full path or remove the higher-priority binary.

### Installer Responsibility
If the installer detects a shadowing condition, it must issue a high-visibility warning to the user:
> *"Warning: An existing installation at /usr/bin/app will hide your new installation at /usr/local/bin/app due to path precedence."*
