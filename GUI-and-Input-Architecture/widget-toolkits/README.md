# 🧱 Tier 1: Widget Toolkits

Widget toolkits represent the highest level of GUI abstraction. Instead of drawing shapes and pixels manually, you organize pre-built native or framework UI controls (widgets) in hierarchical layouts.

---

### 1. The Widget Tree Layout

Widgets are structured as a hierarchical tree. Parent widgets (like Grids, Boxes, or Stacks) calculate the size and coordinates of their child widgets (like Buttons, Inputs, or Labels) recursively.

```text
       [ Window (Root Node) ]
              |
       [ Vertical Box ]
        /            \
 [ Text Input ]    [ Horizontal Box ]
                     /            \
             [ Cancel Button ]  [ Submit Button ]
```

---

### 2. Properties & Event Listeners

*   **Properties**: Widgets contain variables defining their look and state (e.g. `text`, `background_color`, `is_enabled`).
*   **Event Listeners**: Functions bound to user actions (e.g. `onClick()`, `onHover()`, `onTextChanged()`).

---

### 💻 Simple Widget Program in C (GTK 3)

The following C program displays a simple window containing a button that increments a click counter:

```c
#include <gtk/gtk.h>

int counter = 0;

void on_button_clicked(GtkWidget *widget, gpointer label) {
    (void)widget;
    counter++;
    char buffer[32];
    sprintf(buffer, "Clicks: %d", counter);
    gtk_label_set_text(GTK_LABEL(label), buffer); // Update child property
}

int main(int argc, char *argv[]) {
    gtk_init(&argc, &argv);

    // Create container widgets
    GtkWidget *window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
    GtkWidget *vbox = gtk_box_new(GTK_ORIENTATION_VERTICAL, 10);
    GtkWidget *label = gtk_label_new("Clicks: 0");
    GtkWidget *button = gtk_button_new_with_label("Increment");

    // Build the Widget Tree
    gtk_box_pack_start(GTK_BOX(vbox), label, TRUE, TRUE, 0);
    gtk_box_pack_start(GTK_BOX(vbox), button, TRUE, TRUE, 0);
    gtk_container_add(GTK_CONTAINER(window), vbox);

    // Bind event signal
    g_signal_connect(button, "clicked", G_CALLBACK(on_button_clicked), label);
    g_signal_connect(window, "destroy", G_CALLBACK(gtk_main_quit), NULL);

    // Display widgets
    gtk_widget_show_all(window);
    
    // Start GTK Event Loop
    gtk_main();

    return 0;
}
```
