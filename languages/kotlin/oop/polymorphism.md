# Polymorphism (PRO)

Definition: The ability of an object to take on many forms. In Kotlin, this is achieved through interface implementation and method overriding.

## 1. JVM-Legacy (Java-Interop Style)
Dynamic dispatch via interfaces.

```kotlin
interface Drawable { fun draw() }
class Line : Drawable { override fun draw() { } }
```

## 2. Modern Kotlin (K2 / Idiomatic)
Using interfaces with default implementations.

```kotlin
interface Clickable {
    fun click() = println("Click")
}
```

## 3. Kotlin Native (System / C-Interop)
Polymorphism in Native binaries.

```kotlin
fun render(d: Drawable) { d.draw() }
```

## 4. Multiplatform Path (KMP / Common)
Shared interfaces in `commonMain`.

```kotlin
interface Processor { fun process() }
```

## 5. Explicit Path (Strictly Typed)
Explicitly typed polymorphic lists.

```kotlin
val list: List<Drawable> = listOf<Drawable>(Line())
```

# The Logic Bridge
// Logic: Polymorphism relies on the **vtable** (Virtual Method Table). When a method is called on an interface type, the runtime looks up the actual implementation in the object's vtable at execution time, enabling dynamic behavior.
