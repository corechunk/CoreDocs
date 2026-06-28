# 🖼️ 2D Canvas & Loops: Cross-Language Equivalents

This guide maps libraries and frameworks across 7 languages that provide access to raw double-buffered 2D drawing surfaces.

---

### 📊 Language & Library Mapping Table

| Language | Primary 2D Canvas Library | Windowing Layer | Render Pipeline |
| :--- | :--- | :--- | :--- |
| **C** | SDL2 / Raylib | Native OS window handles | Software / OpenGL |
| **C++** | SFML / Cocos2d-x | Native wrappers | OpenGL backend |
| **Rust** | wgpu-rs / pixels | native-windows (winit) | WebGPU / Vulkan / DX12 |
| **Python** | Pygame | SDL2 wrapper | Software / OpenGL |
| **Java** | Java2D / AWT Canvas | JFrame window container | Software / Direct3D (on Windows) |
| **Kotlin** | Skiko | native OS handles | Skia rendering engine (Vulkan/Metal/GL) |
| **JS / TS** | HTML5 `<canvas>` / PixiJS | Web Browser DOM | WebGL / WebGPU acceleration |

---

### 🧠 Overview of equivalent framework options

1.  **C (SDL2 / Raylib)**: Standard low-level multimedia libraries. SDL2 provides raw access to pixel arrays and hardware acceleration. Raylib is a wrapper designed for simple game and graphics prototyping.
2.  **C++ (SFML)**: An object-oriented multimedia library providing classes for sprites, textures, audio, and window management.
3.  **Rust (wgpu-rs / pixels)**: Modern safe abstraction over hardware graphics APIs. `pixels` maps a raw 2D pixel array buffer to a hardware-accelerated texture frame.
4.  **Python (Pygame)**: Standard game programming wrapper library around SDL. Highly beginner friendly, but lacks multi-core parallel scaling due to the Python GIL.
5.  **Java (AWT Canvas / Java2D)**: Standard JDK drawing layer. Uses the `Graphics2D` context to draw text, geometric paths, and images to screen framebuffers.
6.  **Kotlin (Skiko)**: Kotlin bindings for Google's **Skia** graphics engine (the same drawing engine used by Chrome and Android).
7.  **JS / TS (HTML5 Canvas)**: Native web API. Developers retrieve a 2D context (`canvas.getContext("2d")`) to draw vectors and images directly within web pages.
