# Package: javax.swing
## Desktop GUI (Legacy)

Used for creating traditional windowed applications.

### Key Classes
- **JFrame**: The main window.
- **JPanel**: A container for other components.
- **JButton**: A clickable button.
- **JLabel**: Display text or images.
- **JTextField**: Single-line text input.

### Example (Kotlin)
```kotlin
val frame = JFrame("My App")
val button = JButton("Click Me")
frame.add(button)
frame.setSize(300, 200)
frame.isVisible = true
```
