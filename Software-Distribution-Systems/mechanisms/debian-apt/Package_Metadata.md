# Package Metadata & Dependency Control

The `control` file is the heart of a Debian package (`.deb`). It defines how the `apt` and `dpkg` engines handle your software.

## 📄 The `control` File Template

```text
Package: linutils
Version: 1.0.0
Section: utils
Priority: optional
Architecture: all            <-- Use 'all' for Scripts, 'amd64' for Binaries
Maintainer: Developer <developer@email.com>
Depends: bash (>= 5.0), ffmpeg (>= 7.0), gum
Recommends: icon-theme-hicolor
Suggests: yt-dlp
Description: Comprehensive Bash utility suite
 A detailed multiline description must be indented by
 a single space character.
```

---

## ⚖️ Dependency Logic Matrix

| Directive | Impact | Engineering Use-Case |
| :--- | :--- | :--- |
| **`Depends`** | Hard Requirement | Core binaries/libraries (e.g., `ncurses`, `glibc`). |
| **`Recommends`** | Installed by Default | Packages "most users expect" (e.g., optional UI themes). |
| **`Suggests`** | Purely Optional | Enhancements (e.g., a media player for a file manager). |
| **`Conflicts`** | Blocks Install | Packages with the same binary names or incompatible logic. |

---

## 📦 Binary vs. Script Logic

### 1. For Scripts (Bash/Python/etc.)
*   **`Architecture: all`**: Signals that the package works on any CPU (Intel, ARM, etc.).
*   **Dependency:** Usually depends on the interpreter (e.g., `bash`, `python3`).

### 2. For Native Binaries (C/C++/Rust)
*   **`Architecture: amd64`** (or `arm64`): Signals that the binary was compiled for a specific CPU.
*   **Dependency:** Must link to `libc6` and other specific shared libraries found via `ldd`.

---

## 🏗️ State Database (`/var/lib/dpkg/status`)

Debian tracks every installed package in this single text file.
*   **`Status: install ok installed`**: Signals a successful installation.
*   **Auto-Installed Flag**: Managed in `/var/lib/apt/extended_states`. If `Auto-Installed: 1`, the package will be removed when you run `apt autoremove` (if no other apps depend on it).
