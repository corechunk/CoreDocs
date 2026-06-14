# AppDir Structure & Bundling

AppImage is the "AppStore" of Linux. It bundles the application and all its dependencies into a single, self-mounting filesystem volume.

## 📦 The AppDir Layout

To build an AppImage, you must first construct a directory tree (usually named `AppDir/`) with this exact structure:

```text
MyApp.AppDir/
├── AppRun              <-- [EXECUTABLE] Entry point script
├── myapp.desktop       <-- [METADATA] Desktop integration
├── myapp.svg           <-- [ICON] Application icon
└── usr/
    ├── bin/
    │   └── myapp-cli   <-- [BINARY] Your actual tool
    ├── lib/
    │   └── libX.so.1   <-- [DEPS] Bundled shared libraries
    └── share/
        └── icons/ ...
```

---

## 🏃 The `AppRun` Script

The `AppRun` script is the most critical file. It sets up the environment variables so the binary knows to look for libraries **inside the bundle** rather than the host system.

```bash
#!/bin/sh
SELF=$(dirname "$(readlink -f "$0")")
export LD_LIBRARY_PATH="${SELF}/usr/lib:${LD_LIBRARY_PATH}"
export PATH="${SELF}/usr/bin:${PATH}"
exec "${SELF}/usr/bin/myapp-cli" "$@"
```

---

## 🛠️ Automated Bundling with `linuxdeploy`

Manually finding and copying `.so` libraries is painful. Use `linuxdeploy` to automate the process.

1.  **Initialize:** `./linuxdeploy-x86_64.AppImage --appdir MyApp.AppDir`
2.  **Bundle:**
    ```bash
    export DESTDIR=MyApp.AppDir
    make install
    ./linuxdeploy-x86_64.AppImage --appdir MyApp.AppDir --output appimage
    ```

---

## ⚖️ When to use AppImage?
*   **Pros:** Works on almost any distro (Ubuntu, Fedora, Arch, etc.); No root required; Users can keep multiple versions.
*   **Cons:** Large file sizes (because it bundles libraries); FUSE must be installed on the host OS.
