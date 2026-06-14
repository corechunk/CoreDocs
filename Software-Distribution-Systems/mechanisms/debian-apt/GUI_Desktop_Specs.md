# GUI & Desktop Specifications

For graphical applications, packaging requires more than just binaries; you must integrate with the host's Desktop Environment (GNOME, KDE, Hyprland, etc.).

## 🖥️ The `.desktop` Entry
The `.desktop` file tells the OS where to find the app, what icon to use, and how to categorize it in the App Launcher.

**Target Path:** `/usr/share/applications/myapp.desktop`

```ini
[Desktop Entry]
Type=Application
Name=LinUtils GUI
Comment=System optimization dashboard
Exec=/usr/bin/linutils-gui
Icon=linutils
Terminal=false
Categories=Utility;System;
Keywords=optimize;clean;tools;
```

---

## 🎨 Icon Deployment (Hicolor Theme)
Linux uses a standardized icon hierarchy. You should provide icons in multiple sizes.

**Target Path:** `/usr/share/icons/hicolor/`

*   **Raster Icons:**
    *   `/usr/share/icons/hicolor/48x48/apps/myapp.png`
    *   `/usr/share/icons/hicolor/128x128/apps/myapp.png`
*   **Vector Icons (Standard):**
    *   `/usr/share/icons/hicolor/scalable/apps/myapp.svg`

---

## 🏗️ AppStream Metadata
For software centers (like GNOME Software or Discover), you must provide an AppStream XML file. This allows users to see screenshots and detailed descriptions.

**Target Path:** `/usr/share/metainfo/myapp.metainfo.xml`

```xml
<?xml version="1.0" encoding="UTF-8"?>
<component type="desktop-application">
  <id>com.developer.linutils</id>
  <name>LinUtils</name>
  <summary>Extensive system utilities</summary>
  <description>
    <p>A powerful suite of tools to optimize your Linux kernel and UI.</p>
  </description>
  <screenshots>
    <screenshot type="default">
      <caption>The main dashboard</caption>
      <image>https://example.com/screenshot.png</image>
    </screenshot>
  </screenshots>
</component>
```

## 🛠️ Validation Tool
Always validate your desktop files before packaging:
`desktop-file-validate myapp.desktop`
