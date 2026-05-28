# 🎨 Qt Painting: Advanced QPainter (Official)

Advanced coordinate manipulation and high-performance transformation rules.

---

## 1. 📐 The Transformation Pipeline
`QPainter` uses a transformation matrix to map **Logical Coordinates** to **Device Coordinates**.

| Function | Matrix Operation | Description |
| :--- | :--- | :--- |
| `translate(dx, dy)` | Translation | Moves the origin (0,0) to a new position. |
| `rotate(angle)` | Rotation | Rotates the system clockwise (in degrees). |
| `scale(sx, sy)` | Scaling | Multiplies the coordinate values (e.g., 2.0 = 200%). |
| `shear(sh, sv)` | Shearing | Twists the coordinate system. |

## 2. 📝 Complex Coordinate Modes
- **Window:** The logical rectangle used in your code (e.g., "I want to draw in a 1000x1000 grid").
- **Viewport:** The actual physical pixels on the screen (e.g., "Map my grid to this 400x400 widget").
- **Logic:** `painter.setWindow(0, 0, 100, 100)` makes drawing code independent of the physical widget size.

## 3. 🏁 The Logic Bridge
- **Save/Restore:** Always wrap transformations in `painter.save()` and `painter.restore()`. This pushes/pops the current state (Pen, Brush, Matrix) to/from a stack, preventing transformation "leakage."
- **Composition:** Use `setCompositionMode()` to define how new pixels blend with existing ones (e.g., `CompositionMode_Multiply`, `CompositionMode_SourceOver`).

---

[➔ Back to Roadmap](../../core/00-roadmap.md)
