# 🏗️ Qt Widgets: Layout Architecture (Official)

Qt Layouts use a recursive **Size Negotiation Algorithm** to manage widget positions dynamically.

---

## 1. 📐 The Negotiation Algorithm
When a window resizes, the layout engine performs these steps:
1.  **Invalidation:** A child widget calls `updateGeometry()`.
2.  **Constraint Calculation:** The engine queries `minimumSize()`, `sizeHint()`, and `maximumSize()` from every widget.
3.  **Initial Allocation:** Space is assigned based on the **Size Policy**.
4.  **Stretch Distribution:** Remaining "excess" space is divided based on **Stretch Factors**.

## 2. ⚙️ QSizePolicy Rules
Defines how a widget behaves when the layout has more/less space than the `sizeHint`.

| Policy | Growth | Shrink | Description |
| :--- | :--- | :--- | :--- |
| **Fixed** | ❌ No | ❌ No | The `sizeHint` is the only acceptable size. |
| **Minimum** | ✅ Yes | ❌ No | `sizeHint` is the floor. Can expand. |
| **Maximum** | ❌ No | ✅ Yes | `sizeHint` is the ceiling. Can shrink. |
| **Preferred** | ✅ Yes | ✅ Yes | `sizeHint` is ideal; grow/shrink if needed. |
| **Expanding** | ✅ ✅ | ✅ Yes | High "hunger" for extra space. |

## 3. 🏁 The Logic Bridge
- **Height-for-Width:** Use `hasHeightForWidth()` for widgets like word-wrapped labels where the height depends on the current width.
- **Nested Layouts:** A `QLayout` can contain another `QLayout`, which then acts as a single item in the parent negotiation.

---

[➔ Official Guide: Layout Management](https://doc.qt.io/qt-6/layout.html)
[➔ Back to Roadmap](../core/00-roadmap.md)
