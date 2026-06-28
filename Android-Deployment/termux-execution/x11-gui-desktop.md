# 🖥️ Termux X11 & GUI Desktop Environments

Although Termux is primarily a command-line environment, it supports running graphical desktop applications (like GIMP, LibreOffice, or custom GUI applications built with Qt/SDL) by forwarding graphics to an X11 server running locally on the device.

---

### 1. GUI Graphics Architecture

```text
    Termux Terminal (Client)                Termux-X11 App (Server)
+-------------------------------+       +------------------------------+
| Runs GUI Application (Qt/GTK) |       | Receives graphic commands    |
| e.g. DISPLAY=:1 xterm         | ====> | and renders window surface   |
| (Uses X11 protocol over UNIX) |       | on Android touch canvas      |
+-------------------------------+       +------------------------------+
```

---

### 💻 Step-by-Step GUI Setup Guide

Follow this walkthrough to run graphical apps directly on your device:

#### Step 1: Install X11 Package Repository & X11 Server
Within the Termux terminal, enable the X11 package repo and install the X11 system server:
```bash
pkg update
pkg install x11-repo
pkg install termux-x11-nightly
```

#### Step 2: Install a Window Manager (e.g., XFCE)
To manage application windows, install a lightweight desktop environment:
```bash
pkg install xfce4 xfce4-terminal
```

#### Step 3: Run the Termux-X11 App
1. Download and install the **Termux-X11 Android Application** (available on the official GitHub releases or F-Droid).
2. Open the app on your phone. It will initialize a blank canvas and await graphics data on display channel `:1`.

#### Step 4: Start the Desktop Environment
Return to the Termux terminal and launch the display host:
```bash
# 1. Start the X11 server engine in the background
termux-x11 :1 &

# 2. Launch the desktop window manager directed to display channel 1
DISPLAY=:1 xfce4-session
```
Now switch to the Termux-X11 Android app. The full XFCE desktop environment is running on your phone, allowing mouse and keyboard controls.
