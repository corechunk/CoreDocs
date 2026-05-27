# Abstraction (PRO)

Definition: Hiding implementation details and showing only the essential features of an object. Achieved via `abstract` classes and interfaces.

## 1. JVM-Legacy (Java-Interop Style)
Standard abstract classes.

```kotlin
abstract class Component {
    abstract fun render()
}
```

## 2. Modern Kotlin (K2 / Idiomatic)
Using `sealed classes` for restricted hierarchies (Powerful Abstraction).

```kotlin
sealed class UIState {
    object Loading : UIState()
    data class Success(val data: String) : UIState()
}
```

## 3. Kotlin Native (System / C-Interop)
Abstraction in Native code.

```kotlin
abstract class NativeService
```

## 4. Multiplatform Path (KMP / Common)
Shared abstract definitions.

```kotlin
abstract class CommonRepo {
    abstract fun save()
}
```

## 5. Explicit Path (Strictly Typed)
Explicit abstract properties and methods.

```kotlin
abstract class Base {
    abstract val id: Int
    abstract fun init(): Unit
}
```

# The Logic Bridge
// Logic: Abstract classes cannot be instantiated. They serve as templates. `sealed classes` take this further by allowing the compiler to perform exhaustiveness checks in `when` expressions, ensuring all "abstracted" forms are handled.
