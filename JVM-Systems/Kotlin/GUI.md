You have 3 real paths:

---

## 🟢 Option A — Skia / Skiko (modern approach)

👉 Most practical Kotlin-native UI approach today

Used by:

- Compose Multiplatform (desktop UI)

You write Kotlin → it draws via Skia engine.

Example stack:

```
Kotlin/Native → Skia → OpenGL/Vulkan → OS window
```

👉 This is the **modern UI direction**

---

## 🟡 Option B — Compose Multiplatform (recommended)

This is the real answer for “Kotlin Native GUI apps”.

You use:

```
Compose Multiplatform
```

Works on:

- Desktop (Windows/Linux/macOS)
- Android
- (partial iOS via Native)

👉 This is JetBrains’ official UI system

---

## 🔵 Option C — Direct native libraries (low-level)

You can use:

- GLFW (windowing)
- Vulkan / OpenGL (graphics)
- SDL2 (input/audio/window)

via Kotlin/Native C interop.

Example flow:

```
Kotlin/Native → C interop → GLFW → OpenGL
```

This is how game engines start.

---

