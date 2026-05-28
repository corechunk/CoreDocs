# 📊 Qt Widgets: Model/View Architecture (Official)

The **Model/View** pattern separates data from its visual representation, optimized for millions of items.

---

## 1. 🏗️ The Model Interface (`QAbstractItemModel`)
To create a custom model, you MUST implement these core virtual functions:

### Mandatory (List/Table)
- **`rowCount(parent)`**: How many items in the list?
- **`columnCount(parent)`**: (For Tables) How many fields?
- **`data(index, role)`**: Returns the actual value. Common roles: `Qt::DisplayRole`, `Qt::DecorationRole` (Icon), `Qt::EditRole`.

### Mandatory (Hierarchical / Tree)
- **`index(row, col, parent)`**: Generate a unique `QModelIndex` for a node.
- **`parent(child_index)`**: Map a node back to its parent.

## 2. ⛓️ Structural Change Protocol
You MUST notify the views before and after modifying the data structure:
- `beginInsertRows()` / `endInsertRows()`
- `beginRemoveRows()` / `endRemoveRows()`
- `dataChanged(topLeft, bottomRight)`: Notify that specific values were updated.

## 3. 🏁 The Logic Bridge
- **Lazy Loading:** Views only call `data()` for the rows currently visible on the screen.
- **Delegates:** Use `QStyledItemDelegate` to change how items are drawn (e.g., progress bars inside a table cell).
- **Selection:** `QItemSelectionModel` tracks what the user has clicked across multiple views of the same data.

---

[➔ Official Guide: Model/View Programming](https://doc.qt.io/qt-6/model-view-programming.html)
[➔ Back to Roadmap](../core/00-roadmap.md)
