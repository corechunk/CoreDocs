Key topics discussed:

• Android deployment using APK, ADB, and Termux execution.

• Library and framework philosophy.

• SDL vs Qt and high-level vs low-level architectural approaches.

• Custom drawing and input event logic bridging desktop and Android.


# UI Input Handling & Library Linking Strategy

## 1. Unified Input: Mouse Click to Touch Translation
To maintain a single codebase for both Windows/Linux (Desktop) and Android (Mobile), input handling must abstract the difference between hardware mouse clicks and capacitive screen touches.

* **SDL Input Abstraction:** SDL automatically translates standard, single-finger touch events into synthetic mouse events by default (`SDL_MOUSEBUTTONDOWN`, `SDL_MOUSEBUTTONUP`, `SDL_MOUSEMOTION`).
* **The Desktop vs. Mobile Challenge:** * On Desktop, you must track mouse hovering and distinct left/right clicks to interact with your custom top ribbon or UI elements.
    * On Mobile, "hovering" does not exist, and right-clicks are generally unavailable. Everything relies on tap, drag, or multi-touch gestures.
* **Implementation Strategy:**
    1.  **Use Immediate-Mode UI (Dear ImGui):** ImGui abstracts this beautifully. If you pass SDL's mouse events into ImGui's backend handler, ImGui handles the sizing, hitboxes, and clicks seamlessly. A finger tap on Android will automatically trigger an ImGui button press exactly like a mouse click on Windows.
    2.  **Custom Hitboxes for the Top Ribbon:** If handling manually in SDL, define basic geometric collision blocks (`SDL_Rect`). Track finger/mouse coordinates uniformly on click/tap events to determine if the user pressed the close, maximize, or minimize regions.

---

## 2. Cross-Compilation & Dynamic Linking

When deploying a cross-platform C/C++ application, you cannot use a desktop-compiled binary (like a `.lib` or `.dll` on Windows, or an `.a`/`.so` on x86_64 Linux) for an Android target. Android devices primarily utilize ARM architectures (ARMv7 or ARM64).

### Building the Dynamic Libraries (`.so`)
* **The Android NDK (Native Development Kit):** You must use the NDK toolchain along with CMake or the provided build scripts of SDL/Dear ImGui to cross-compile the libraries from your desktop machine into Android-compatible shared object (`.so`) binaries.
* **Architectures:** Ensure you cross-compile for the target architecture of the mobile device, typically `arm64-v8a` for modern devices and `armeabi-v7a` for older hardware.

### Linking Mechanics in the Project Setup
* **Desktop (Windows/Linux):** You link your source files against the desktop version of the libraries. On Windows, this means linking against `.lib` files at compile-time and placing `.dll` files in the executable directory at runtime. On Linux, you link against `.so` files using your system compiler.
* **Android (Gradle & CMake Integration):** 1.  Place your cross-compiled `.so` binaries inside your Android project structure (typically under `app/src/main/jniLibs/arm64-v8a/`).
    2.  Configure your `CMakeLists.txt` inside the Android project to find and link these prebuilt libraries using the `target_link_libraries` command.
    3.  When Gradle compiles the project into an APK, it packages these dynamic binaries inside the payload, allowing the Android runtime to load them via `System.loadLibrary("SDL3")` or your respective module names when the app launches.
    4. 


