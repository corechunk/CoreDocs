# Inheritance (PRO)

Definition: Deriving a new class from an existing class to reuse and extend functionality. Kotlin classes are `final` by default.

## 1. JVM-Legacy (Java-Interop Style)
Standard inheritance via `open`.

```kotlin
open class Animal
class Dog : Animal()
```

## 2. Modern Kotlin (K2 / Idiomatic)
Inheritance with primary constructor mapping.

```kotlin
open class Shape(val color: String)
class Circle(color: String, val radius: Int) : Shape(color)
```

## 3. Kotlin Native (System / C-Interop)
Inheritance in Native objects.

```kotlin
open class NativeBase
```

## 4. Multiplatform Path (KMP / Common)
Shared hierarchies and `expect`/`actual` inheritance.

```kotlin
expect open class PlatformBase()
```

## 5. Explicit Path (Strictly Typed)
Explicit overrides and constructor calls.

```kotlin
open class Base constructor(id: Int)
class Derived : Base {
    constructor(id: Int) : super(id)
    override fun toString(): String = "Derived"
}
```

# The Logic Bridge
// Logic: Kotlin uses the `open` keyword to explicitly allow inheritance, adhering to the "Design for inheritance or prohibit it" principle. At the VM level, this translates to the absence of the `final` flag on the class and methods.
