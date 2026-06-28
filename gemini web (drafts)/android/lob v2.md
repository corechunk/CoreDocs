# GUI Development Path & Window Architecture

## 1. Roadmap: Libraries & Frameworks

### Option 1: Core Fundamentals (SDL 2 / SDL 3)
* **Focus:** Low-level window creation, input handling, event looping, and raw canvas/renderer setup.
* **Goal:** Master the absolute basics of handling cross-platform hardware contexts (Windows, Linux, macOS, Android, iOS) without external UI clutter.

### Option 2: UI Expansion (Dear ImGui + SDL Backend)
* **Focus:** Overlaying an immediate-mode GUI layer on top of your existing SDL window.
* **Goal:** Eliminate manual widget/button rendering and resizing math. Leverage Dear ImGui’s internal systems for tools, debug menus, or game interfaces while retaining SDL for the underlying engine backend.

### Option 3: Advanced Ecosystems (Qt or Diverse Backends)
* **Focus:** Transitioning to Qt for complex, heavy-duty desktop applications, or decoupling Dear ImGui from SDL to bind it directly to raw OpenGL ES, Vulkan, or DirectX.
* **Goal:** Full architectural flexibility depending on target requirements.

---

## 2. Cross-Platform Window Architecture

### The Borderless Canvas Strategy
Instead of relying on native operating system decorations (which look completely different on desktop and are nonexistent on mobile), you initialize a **borderless window** across all target platforms. 

* **Desktop Behaviour:** Launches as a borderless window that you can manually size or maximize to fill the screen space.
* **Mobile Behaviour (Android/iOS):** Automatically initializes as a native, full-screen canvas covering the display view, respecting the platform's lifecycle.

### Conditional Ribbon Logic
Since the entire window is now a single, raw drawing canvas, your custom top navigation bar (close, minimize, maximize buttons, and window titles) is drawn inside your application logic using conditional compilation or runtime checks.

```cpp
// Pseudocode for layout rendering loop
void RenderApplication() {
    // Check target platform at runtime
    const char* platform = SDL_GetPlatform();
    
    if (SDL_strcmp(platform, "Windows") == 0 || 
        SDL_strcmp(platform, "Linux") == 0 || 
        SDL_strcmp(platform, "Mac OS X") == 0) {
        
        // 1. Draw Custom Window Controls & Top Ribbon for Desktop
        DrawCustomTopRibbon(); 
        
        // 2. Render Main App/Game Canvas below the ribbon
        RenderMainContent(0, RIBBON_HEIGHT, WINDOW_WIDTH, WINDOW_HEIGHT - RIBBON_HEIGHT);
    } else {
        // 3. Mobile Environment (Android/iOS) - Skip ribbon, use full screen
        RenderMainContent(0, 0, WINDOW_WIDTH, WINDOW_HEIGHT);
    }
}
