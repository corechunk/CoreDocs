# 🏛️ [Master Kotlin Reference (One-Shot)](master-kotlin.md)

# 🏗️ The "Penta-Snippet" Golden Standard
Every topic (especially **[CORE]** topics) must follow this 5-step implementation logic to ensure a total systems-level understanding:

1.  **JVM-Legacy (Java-Interop Style):** The verbose, Java-like way. Highlighting how Kotlin maps to or interacts with traditional JVM patterns.
2.  **Modern Kotlin (K2 / Idiomatic):** The high-level "Auto" path. Using K2's latest syntax and power.
3.  **Kotlin Native (System / C-Interop):** The "Metal" path. Using POSIX APIs or C-interop (e.g., `platform.posix.*`) to interact with the OS.
4.  **Multiplatform Path (KMP / Common):** The "Portable" path. Strictly `commonMain` compatible code.
5.  **Explicit Path (Strictly Typed):** The "Strict" path. Manually declaring every type and modifier to remove compiler "magic."

# 🧭 Universal Language Blueprint: Tiered Learning (v2) - Kotlin Edition

This roadmap groups the 53 universal language topics by **Mastery Tier**. Numbering inside `[]` restarts from 01 in each category.

---

## 🟢 Tier 1: The Foundation [CORE]
*The non-skippable essentials. Master these to write functional, correct code.*

### Environment & Setup
- [Toolchain Installation](./setup/00-start.md) (Installation, `mise`, PATH, Kotlin/Native)
- [Compilation & Run Basics](./setup/01-compile-run.md) (kotlinc, gradle, K2 runner)

### Lexical & Data
- [Tokens & Lexemes](./04-tokens-lexemes.md) (Atoms of the language)
- [Keywords & Standards](./05-keywords-standards.md) (Kotlin 2.0 Standards)
- [Comments & Metadata](./07-comments-metadata.md) (KDoc, Annotations)
- [Variables & Constants](./08-variables-constants.md) (val vs var vs const)
- [Data Types](./09-data-types.md) (Conceptual Hub)
    - [Integers](./data-type/integers.md)
    - [Floats](./data-type/floats.md)
    - [Unsigned](./data-type/unsigned.md)
    - [Special Types](./data-type/nothing-unit.md)
- [String Escaping](./10-string-escaping.md)
- [Interpolation](./11-interpolation.md) ($Variable substitution)
- [Scope & Lifetime](./12-scope-lifetime.md) (Shadowing, Visibility modifiers)

### Logic & Control
- [Operators](./17-operators.md) (Conceptual Hub)
    - [Math](./operator/math.md)
    - [Logical](./operator/logical.md)
    - [Bitwise](./operator/bitwise.md)
    - [Assignment](./operator/assignment.md)
- [Precedence & Associativity](./18-precedence-associativity.md)
- [Expressions & Statements](./19-expressions-statements.md) (Everything is an expression)
- [Type Casting](./21-type-casting.md) (Smart casts)
- [Truth Rule](./22-truth-rule.md) (Strict Booleans)
- [Conditionals](./22-conditionals.md) (Conceptual Hub)
    - [If Expression](./control/if.md)
    - [When Expression](./control/when.md)
- [Iteration: Definite](./23-iteration-definite.md) (For loops, ranges)
- [Iteration: Indefinite](./24-iteration-indefinite.md) (While, do-while)

### The Function Engine
- [Function Basics](./26-function-basics.md)
- [Return Types](./27-function-basics.md)
- [Recursion](./28-recursion.md) (tailrec optimization)
- [Passing Mechanisms](./29-passing-mechanisms.md) (Value vs Reference)

### Architecture & Environment
- [Sequential Collections](./31-sequential-collections.md) (Conceptual Hub)
    - [Fixed Arrays](./array/fixed.md)
    - [Lists](./array/lists.md)
- [Associative Collections](./32-associative-collections.md) (Maps, Sets)
- [Structs Base](./33-structs-base.md) (Data Classes)
- [Class Concept](./35-class-concept.md) (Primary vs Secondary constructors)
- [IO Streams](./37-io-streams.md) (println, Scanner, readln)
- [Error Handling](./42-error-handling.md) (Exceptions, Result type)

---

## 🔵 Tier 2: Idiomatic Power [PRO]
*Native techniques and efficiency. Master these to write "Professional" code.*

### Efficiency & Native Power
- [Tuning & Strictness](./06-tuning-strictness.md) (Compiler options, Opt-in)
- [Native Strings](./14-native-strings.md) (TrimIndent, Raw strings)
- [Pattern Matching](./15-pattern-matching.md) (When expressions)
- [Jump Statements](./25-jump-statements.md) (Labels, Return@label)
- [Closures & Lambdas](./30-closures-lambdas.md) (Higher-order functions)

### Advanced Redirections
- [Procedural Mechanisms](./procedural/00-start.md) (Conceptual Hub)
    - [Top-Level Execution](./procedural/top-level.md)
    - [Extension Functions](./procedural/extensions.md)
- [Advanced OOP](./oop/00-start.md) (Conceptual Hub)
    - [Encapsulation](./oop/encapsulation.md)
    - [Inheritance](./oop/inheritance.md)
    - [Polymorphism](./oop/polymorphism.md)
    - [Abstraction](./oop/abstraction.md)
    - [Objects & Companions](./oop/objects.md)
- [Async & Coroutines](./concurrency/03-async.md) (Suspending functions)
- [HTTP Client API](./network/03-http.md) (Ktor client)
- [Redirection & Piping](./38-redirection-piping.md) (Standard Library extensions)

### Project Lifecycle & Build
- [Multi-File Projects](./build/00-start.md)
- [Build Tools](./build/01-tools.md) (Gradle KTS)
- [Standard Library](./45-standard-library.md) (Scope functions: let, run, etc.)

---

## 🔴 Tier 3: Advanced Internals [SYSTEMS]
*The engine and the OS. Master these to build systems, compilers, or drivers.*

### Internals & Memory
- [Charset](./03-charset.md) (UTF-16 JVM vs UTF-8 Native)
- [Storage Classes](./13-storage-classes.md) (lateinit, by lazy)
- [Syntactic Automation](./16-syntactic-automation.md) (Inline classes, Reified types)
- [Synchronization](./concurrency/04-sync.md) (Mutex, Volatile)
- [Exit Codes & Signals](./39-exit-codes-signals.md) (JVM hooks)
- [Memory Management](./memory/00-start.md) (Conceptual Hub)
    - [Stack vs Heap](./memory/stack-heap.md)
    - [Allocation](./memory/allocation.md)
- [Pointer Mastery](./41-pointer-mastery.md) (C-Interop/COpaquePointer)

### Low-Level Concurrency
- [Process Forking](./concurrency/01-forking.md) (ProcessBuilder)
- [Multi-Threading](./concurrency/02-threads.md) (Executors, Dispatchers)

### Low-Level Networking
- [Socket Basics](./network/01-sockets.md) (Java Sockets)
- [Protocols: TCP & UDP](./network/02-protocols.md) (Ktor Raw Sockets)

### Toolchain Lifecycle
- [Linking & Delivery](./build/02-linking.md) (Fat Jar vs Native Binary)
