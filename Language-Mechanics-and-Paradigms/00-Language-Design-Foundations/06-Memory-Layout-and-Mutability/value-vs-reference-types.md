# 💾 Value vs. Reference Types

## 1. Value Types (Primitives & Structs)
Allocated continuously directly within current execution thread **Stack frames**. Copying a value type duplicates the raw bytes.

## 2. Reference Types
Allocated dynamically inside managed **Heap pools**. Variables contain memory addresses (pointers) referencing the underlying heap object.
