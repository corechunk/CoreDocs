# 🎨 Qt Painting: QPainter Basics (Official)

The standard 2D vector graphics interface. `QPainter` translates logical drawing commands into physical device pixels.

---

## 1. 🏗️ The Paint Logic
Custom drawing MUST occur within the `paintEvent(QPaintEvent*)` of a `QWidget` or `QPaintDevice`.

```cpp
void MyWidget::paintEvent(QPaintEvent *event) {
    QPainter painter(this); // Initializes for this widget
    
    // 1. Set the Tool (Pen = Outline)
    QPen pen(Qt::blue, 3, Qt::DashLine, Qt::RoundCap, Qt::MiterJoin);
    painter.setPen(pen);
    
    // 2. Set the Material (Brush = Fill)
    QBrush brush(Qt::green, Qt::SolidPattern);
    painter.setBrush(brush);
    
    // 3. Draw Primitives
    painter.drawRect(rect().adjusted(10, 10, -10, -10));
}
```

## 2. 🛠️ The Complete Drawing Matrix
| Category | Functions | Purpose |
| :--- | :--- | :--- |
| **Primitives** | `drawPoint()`, `drawLine()`, `drawRect()`, `drawEllipse()`, `drawPolyline()` | Outlines of basic geometric shapes. |
| **Complex** | `drawArc()`, `drawPie()`, `drawChord()`, `drawPolygon()`, `drawConvexPolygon()` | Advanced curves and closed shapes. |
| **Paths** | `drawPath()`, `fillPath()`, `strokePath()` | Render complex `QPainterPath` (Bézier curves). |
| **Text** | `drawText()`, `drawStaticText()`, `drawGlyphRun()` | High-performance text and custom layouts. |
| **Images** | `drawPixmap()`, `drawImage()`, `drawTiledPixmap()`, `drawPixmapFragments()` | Raster image display and particle systems. |
| **Direct Fill** | `fillRect()`, `eraseRect()` | Fill areas directly without pen/outline step. |

## 3. 🏁 The Logic Bridge
- **Immediate Mode:** Drawing is transient. Every time `update()` is called, the entire scene is re-executed.
- **Cosmetic Pen:** A pen with width **0** is "cosmetic"—it remains 1 pixel wide regardless of scaling or transformations.
- **Antialiasing:** Enable `painter.setRenderHint(QPainter::Antialiasing)` for smooth edges on diagonal lines and curves.

---

[➔ Official API: QPainter](https://doc.qt.io/qt-6/qpainter.html)
[➔ Back to Roadmap](../core/00-roadmap.md)
