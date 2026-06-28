# 🏛️ Nominal vs. Structural Typing (OOP Boundaries)

## 1. Nominal Typing (Java, C++)
Compatibility is dictated strictly by explicit type names and inheritance trees. A class must explicitly implement an interface to be accepted.

## 2. Structural Typing (TypeScript, Go)
Compatibility is based entirely on the shape (fields and signatures) of the data layout.

## 3. Base Engine v1.0 Architectural Constraint
For high-performance systems engineering and initial language engine versions, **Base Engine v1.0 bounds data layouts strictly to C-style `struct` containers**. Full OOP classes, inheritance, and Virtual Method Tables (`vtables`) are excluded to prevent dynamic dispatch performance overhead.
