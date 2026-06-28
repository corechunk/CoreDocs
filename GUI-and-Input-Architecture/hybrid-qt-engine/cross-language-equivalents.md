# 🧬 Hybrid Engines: Cross-Language Equivalents

This guide maps hybrid visual architectures (mixing declarative UI layouts with compiled system backends) across 7 mainstream languages.

---

### 📊 Language & Library Mapping Table

| Language | Hybrid Framework | Frontend Language | Backend Language | Rendering Engine |
| :--- | :--- | :--- | :--- | :--- |
| **C** | IUP with Webview | HTML / JS | C (raw bindings) | Native Web View Context |
| **C++** | Qt Quick | QML / JavaScript | C++ (native classes) | Qt Scene Graph (Vulkan/GL) |
| **Rust** | Tauri | HTML / CSS / JS | Rust (system calls) | Native Web View (WebKit/WebView2) |
| **Python** | PyQt5 / PySide6 | QML / JavaScript | Python controllers | Qt Scene Graph |
| **Java** | JavaFX | FXML / CSS | Java controller classes | Prism (Vulkan/Metal/DX backend) |
| **Kotlin** | Compose Multiplatform | Kotlin Declarative | Kotlin systems JVM | Skia Graphics Context |
| **JS / TS** | Electron / Tauri | HTML / CSS / JS | Node.js / Rust | Chromium (Electron) / WebView |

---

### 🧠 Overview of equivalent framework options

1.  **C (IUP Webview)**: Due to lack of native declarative languages in standard C, hybrid development is handled by embedding web engine windows (Webviews) that interface with C callback functions.
2.  **C++ (Qt Quick)**: The industry standard. Combines QML layout architectures with C++ logic loops, communicating via Qt's meta-object signal-and-slot system.
3.  **Rust (Tauri)**: An ultra-lightweight alternative to Electron. The UI frontend is constructed using standard web technologies (React, Vue, Svelte), which make system-level calls to a Rust backend via JSON RPC protocols.
4.  **Python (PySide)**: Accesses the full Qt QML engine. UI parameters are defined in `.qml` files and loaded via PySide Python objects.
5.  **Java (JavaFX)**: Splits design files (`.fxml` XML format) from Java event controllers, utilizing standard CSS for custom UI styling.
6.  **Kotlin (Compose)**: Uses Kotlin to write both the declarative UI layout and backend data streams, utilizing Skia to render pixel frames.
7.  **JS (Electron)**: Bundles a complete Chromium browser instance with Node.js. Allows standard web dev frameworks to access system-level OS features, but has high memory and storage footprints.
