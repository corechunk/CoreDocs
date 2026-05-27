# Advanced OOP (PRO - Hub)

Definition: Interfaces, inheritance, and abstract classes.

## Deep-Dive Reference
For complex hierarchies and abstractions:
- [Encapsulation](./encapsulation.md) | [Inheritance](./inheritance.md)
- [Polymorphism](./polymorphism.md) | [Abstraction](./abstraction.md)
- [Objects & Companions](objects.md)

---

## 1. JVM-Legacy (Java-Interop Style)
Standard inheritance.

```kotlin
open class Base
class Derived : Base()
```

## 2. Modern Kotlin (K2 / Idiomatic)
Interfaces with default implementations.

```kotlin
interface Clickable {
    fun click() = println("Clicked")
}
```

## 3. Kotlin Native (System / C-Interop)
OOP in Native code.

```kotlin
class NativeObject
```

## 4. Multiplatform Path (KMP / Common)
Shared interfaces and sealed classes.

```kotlin
sealed class State
```

## 5. Explicit Path (Strictly Typed)
Explicit overrides.

```kotlin
class C : Clickable {
    override fun click() { super.click() }
}
```

# The Logic Bridge
// Logic: Kotlin uses `open` to allow inheritance, as classes are final by default. Interfaces can contain property declarations and method bodies.
