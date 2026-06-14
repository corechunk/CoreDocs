# Windows Git Bash & Scoop

Windows lacks a native POSIX subsystem. Distributing Bash TUI apps requires a compatibility layer (Git Bash) and unique path/terminal handling.

## 🌉 The Git Bash Compatibility Layer
Git Bash (MSYS2) provides a virtual root (`/`) that maps to Windows drives.

### 1. Path Translation (`cygpath`)
Windows uses `C:\Path`, but Bash expects `/c/Path`. Passing a Unix path to a native Windows tool (like `ffmpeg.exe`) will cause a crash.

**The Fix:**
```bash
if [[ "$OSTYPE" == "msys" ]]; then
    # Convert Unix path to Windows 'W'indows format
    NATIVE_PATH=$(cygpath -w "/c/Users/Public/video.mp4")
fi
```

### 2. TTY & TUI Failures (`winpty`)
The Git Bash terminal (**MinTTY**) does not emulate a standard Unix TTY. Interactive TUI tools (like `gum`, `dialog`, or `fzf`) will freeze because they cannot read stdin correctly.

**The Fix:** Wrap interactive commands in `winpty`.
```bash
# Check if running in a MinTTY pty
if [[ "$TERM" == "xterm" ]] && [[ "$OSTYPE" == "msys" ]]; then
    EXEC_WRAPPER="winpty"
fi
$EXEC_WRAPPER gum choose "Option A" "Option B"
```

---

## 🍦 Windows Package Managers (Scoop)
Scoop is the best way to distribute CLI tools on Windows. It is user-space only and handles environment `PATH` automatically.

### Scoop Manifest (`linutils.json`)
```json
{
    "version": "1.0.0",
    "url": "https://github.com/developer/linutils/archive/v1.0.0.zip",
    "extract_dir": "linutils-1.0.0",
    "bin": "bin/linutils.sh",
    "depends": "git-bash",
    "notes": "Ensure you run this inside a Git Bash terminal."
}
```

---

## 🛠️ Summary of Windows Quirks
| Issue | Tool/Fix |
| :--- | :--- |
| **Path Mismatch** | `cygpath -w` |
| **TUI/Terminal Freeze** | `winpty` |
| **Line Endings** | Ensure scripts use `LF` (Unix) not `CRLF` (Windows). |
| **Permissions** | Windows uses `attrib` or ACLs; `chmod +x` is emulated by Git Bash. |
