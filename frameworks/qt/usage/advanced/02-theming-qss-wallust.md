# 🎨 Qt Advanced: Theming & Wallust (Official)

Achieving elite aesthetics through the **Qt Style Sheet (QSS)** engine and dynamic system integration.

---

## 1. 🏗️ Qt Style Sheets (QSS)
QSS is a subset of CSS specifically for styling `QtWidgets`.

### The Box Model
Like web CSS, every widget has a Content area, Padding, Border, and Margin.

```css
QPushButton {
    background-color: #2e3440; /* Nord Theme */
    border: 2px solid #4c566a;
    border-radius: 8px;
    padding: 5px 15px;
    color: #eceff4;
}

QPushButton:hover { background-color: #3b4252; }
QPushButton:pressed { background-color: #434c5e; }
```

## 2. ⚡ Wallust & Dynamic Theming
To bridge your system colors into Qt:
1.  **Generate:** `wallust run image.png` (Creates `~/.cache/wallust/colors.css`).
2.  **Inject:** Apply the style sheet at runtime.

```cpp
QFile file(QDir::homePath() + "/.cache/wallust/colors.css");
if (file.open(QFile::ReadOnly)) {
    qApp->setStyleSheet(file.readAll());
}
```

## 3. 🏁 The Logic Bridge
- **Selectors:** You can target by Class (`QPushButton`), Object Name (`#mySpecificButton`), or Property (`[urgent="true"]`).
- **Performance:** Complex stylesheets can slow down startup. For heavy UIs, consider using **QPalette** for colors and QSS only for borders/geometry.

---

[➔ Back to Roadmap](../../core/00-roadmap.md)
