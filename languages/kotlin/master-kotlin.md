# Master Kotlin Reference (One-Shot)

Definition: A high-density reference guide for Kotlin development across JVM, Native, and Multiplatform.

## CORE Logic
- **Variables:** `val` (immutable), `var` (mutable), `const val` (compile-time).
- **Types:** Everything is an object; optimized to primitives on JVM.
- **Control Flow:** `if` and `when` are expressions.
- **Functions:** First-class citizens; support for extensions and lambdas.

## PRO Idioms
- **Null Safety:** `String?`, `?.`, `!!`, `?:`.
- **Scope Functions:** `let`, `also`, `run`, `apply`, `with`.
- **Delegation:** `by lazy`, `by Delegates.observable`.

## SYSTEMS Internals
- **Coroutines:** Non-blocking async via state machines.
- **Memory:** GC-managed; manual memory in Native via `memScoped`.
- **K2 Compiler:** Rewritten frontend for faster and smarter compilation.

# The Logic Bridge
// Logic: Kotlin bridges the gap between high-level expressive code and low-level performance, providing a unified developer experience from backend servers to native systems.
