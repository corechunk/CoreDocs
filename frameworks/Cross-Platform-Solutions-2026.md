# Cross-Platform Solutions (2026 Gold Mark Reference)

## 🏁 The Landscape (Native vs. Custom Rendering)
In 2026, the cross-platform world is split into two philosophies:
1. **Native Webview/Logic Sharing:** (Tauri, KMP) Uses the system's own tools to keep things light.
2. **Custom Rendering Engines:** (Compose MP, Qt, Slint) Draws every pixel themselves for 100% control.

---

## 🏆 The "Gold Mark" Trinity

### 1. Tauri 2.0 (Rust + Webview)
*   **Concept:** The "Electron Killer." Uses the OS's native WebView (WebKit/WebView2) with a **Rust** backend.
*   **Performance:** Ultra-lightweight. Binary sizes often <10MB.
*   **Nativeness:** Uses system-provided UI engines. No bundled browser.
*   **Mobile:** Stable support for Android and iOS as of 2.0.
*   **Best For:** Web devs who want extreme efficiency and Rust's safety.

### 2. Kotlin Multiplatform & Compose Multiplatform (Kotlin)
*   **Concept:** **KMP** shares logic; **Compose MP** shares the UI.
*   **Performance:** Native performance. Compiles to JVM/Native binaries.
*   **Nativeness:** Uses Skia (GPU) to render UI at 120Hz. High fidelity.
*   **Mobile:** Production-ready for Android and iOS.
*   **Best For:** Android-first teams and sharing 95%+ of code without compromise.

### 3. Qt 6.x (C++ / QML)
*   **Concept:** The industrial heavy-hitter. Powered by C++ and QML.
*   **Performance:** The standard for professional creative/industrial tools.
*   **Nativeness:** Mature, stable, but "heavier" than modern alternatives.
*   **Mobile:** Mature support for Android/iOS.
*   **Best For:** Industrial, medical, or complex professional desktop/mobile apps.

---

## 🌟 The Elite Niche

### Slint (Rust / C++)
*   **Focus:** Extreme efficiency (can run on 300KB RAM).
*   **Nativeness:** Compiles directly to C++/Rust code.
*   **Mobile:** Supports Android/iOS via Rust.
*   **Best For:** Embedded systems and ultra-lightweight system utilities.

### GPUI (Rust)
*   **Focus:** GPU-accelerated UI (rendered like a video game).
*   **Nativeness:** Hand-crafted for ultra-low latency.
*   **Status:** Emerging for mobile; revolutionary for desktop editors (e.g., Zed).

---

## 📊 Technical Comparison Matrix

| Metric | Tauri 2.0 | Compose MP | Qt 6.x | Slint |
| :--- | :--- | :--- | :--- | :--- |
| **Language** | Rust / JS | Kotlin | C++ / QML | Rust / C++ |
| **Binary Size** | Tiny (<10MB) | Medium (~15MB) | Large (50MB+) | Tiny (<5MB) |
| **RAM Usage** | Low | Moderate | High | Ultra-Low |
| **Rendering** | WebView | Skia (GPU) | Native/GL | Software/GL |
| **Mobile Status**| Stable | Stable | Mature | Emerging |

---

## 🎯 Strategic Recommendation
*   **Maximum Mobile Native Feel:** Use **Kotlin Multiplatform (Compose)**.
*   **Smallest Binary / Best Security:** Use **Tauri 2.0**.
*   **Ultra-Performance System Tool:** Use **Slint** or **GPUI**.
*   **Industrial Stability:** Use **Qt**.
