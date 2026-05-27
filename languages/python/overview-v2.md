# 🏛️ [Master Python Reference (One-Shot)](master-python.md)

# 🏗️ The "Systems-Python" Quad-Snippet Standard
Every topic (especially **[CORE]** topics) must follow this 4-step implementation logic to ensure a total systems-level understanding:

1.  **Modern Path (3.12+ / Idiomatic):** The high-level "Auto" path using latest features like Structural Pattern Matching and modern f-strings.
2.  **Systems Path (Internals / C-Interop):** The "Metal" path. Using `ctypes`, `struct`, or `dis` to show how Python interacts with C or the VM Bytecode.
3.  **Portable Path (Zero-Dependency):** Strictly using the Python Standard Library. No `pip` needed.
4.  **Strict Path (Type-Hinted):** The "Strict" path. Using `typing` and `mypy` standards to enforce rigidity and remove dynamic ambiguity.

# 🧭 Universal Language Blueprint: Tiered Learning (v2) - Python Edition

This roadmap groups the 53 universal language topics by **Mastery Tier**. Numbering inside `[]` restarts from 01 in each category.

---

## 🟢 Tier 1: The Foundation [CORE]
*The non-skippable essentials. Master these to write functional, correct code.*

### Environment & Setup
- [Toolchain Installation](./setup/01-toolchain.md) (Installation, `mise`, PATH)
- [Compilation & Run Basics](./setup/02-compile-run.md) (Interpreter, Bytecode, `.pyc`)

### Lexical & Data
- [Tokens & Lexemes](./04-tokens-lexemes.md) (Indentation, Identifiers)
- [Keywords & Standards](./05-keywords-standards.md) (Reserved words)
- [Comments & Metadata](./07-comments-metadata.md) (Docstrings, Type hints)
- [Variables & Constants](./08-variables-constants.md) (Naming, `Final`)
- [Data Types](./09-data-types.md) (Everything is an Object)
    - [Integers](./data-type/integers.md)
    - [Floats](./data-type/floats.md)
    - [Booleans](./data-type/booleans.md)
    - [Special Types](./data-type/none-type.md)
- [String Escaping](./10-string-escaping.md)
- [Interpolation](./11-interpolation.md) (f-strings)
- [Scope & Lifetime](./12-scope-lifetime.md) (LEGB Rule)

### Logic & Control
- [Operators](./17-operators.md) (Conceptual Hub)
    - [Math](./operator/math.md)
    - [Bitwise](./operator/bitwise.md)
- [Precedence & Associativity](./18-precedence-associativity.md)
- [Expressions & Statements](./19-expressions-statements.md) (Statement-based syntax)
- [Type Casting](./21-type-casting.md) (Coercion, Explicit casting)
- [Truth Rule](./22-truth-rule.md) (Truthiness)
- [Conditionals](./22-conditionals.md) (Conceptual Hub)
    - [If Expression](./control/if.md)
    - [Match Expression](./control/match.md)
- [Iteration: Definite](./23-iteration-definite.md) (For loops, ranges)
- [Iteration: Indefinite](./24-iteration-indefinite.md) (While loops)

### The Function Engine
- [Function Basics](./26-function-basics.md)
- [Return Types](./27-function-basics.md)
- [Recursion](./28-recursion.md) (Recursion limit)
- [Passing Mechanisms](./29-passing-mechanisms.md) (Pass-by-Object-Reference)

### Architecture & Environment
- [Sequential Collections](./31-sequential-collections.md) (Conceptual Hub)
    - [Lists](./array/lists.md)
    - [Tuples](./array/tuples.md)
- [Associative Collections](./32-associative-collections.md) (Dicts, Sets)
- [Structs Base](./33-structs-base.md) (NamedTuple, Dataclasses)
- [Class Concept](./35-class-concept.md) (`__init__`, `self`)
- [IO Streams](./37-io-streams.md) (stdin, stdout, stderr)
- [Error Handling](./42-error-handling.md) (Try-Except)

---

## 🔵 Tier 2: Idiomatic Power [PRO]
*Native techniques and efficiency. Master these to write "Professional" code.*

### Efficiency & Native Power
- [Tuning & Strictness](./06-tuning-strictness.md) (Static analysis)
- [Native Strings](./14-native-strings.md) (Methods, Slicing)
- [Pattern Matching](./15-pattern-matching.md) (Structural Matching)
- [Jump Statements](./25-jump-statements.md) (Break, Continue)
- [Closures & Lambdas](./30-closures-lambdas.md) (Decorators)

### Advanced Redirections
- [Procedural Mechanisms](./procedural/00-start.md) (Conceptual Hub)
    - [Modules](./procedural/modules.md)
    - [Packages](./procedural/packages.md)
    - [Top-Level Execution](./procedural/top-level.md)
- [Advanced OOP](./oop/00-start.md) (Conceptual Hub)
    - [Encapsulation](./oop/encapsulation.md)
    - [Inheritance](./oop/inheritance.md)
    - [Polymorphism](./oop/polymorphism.md)
    - [Abstraction](./oop/abstract-classes.md)
    - [Mixins & MRO](./oop/mixins.md)
- [Async & Coroutines](./concurrency/03-async.md) (`asyncio`)
- [HTTP Client API](./network/03-http.md) (`urllib`, `requests`)
- [Redirection & Piping](./38-redirection-piping.md) (Subprocess)

### Project Lifecycle & Build
- [Multi-File Projects](./build/00-start.md)
- [Build Tools](./build/01-tools.md) (`venv`, `poetry`)
- [Standard Library](./45-standard-library.md) (Key modules)

---

## 🔴 Tier 3: Advanced Internals [SYSTEMS]
*The engine and the OS. Master these to build systems, compilers, or drivers.*

### Internals & Memory
- [Charset](./03-charset.md) (UTF-8, Unicode)
- [Storage Classes](./13-storage-classes.md) (Global, Nonlocal)
- [Syntactic Automation](./16-syntactic-automation.md) (Metaclasses)
- [Synchronization](./concurrency/04-sync.md) (The GIL, Locks)
- [Exit Codes & Signals](./39-exit-codes-signals.md) (`sys.exit`, `signal`)
- [Memory Management](./memory/00-start.md) (Conceptual Hub)
    - [Stack vs Heap](./memory/stack-heap.md)
    - [Allocation](./memory/allocation.md) (Ref counting)
- [Pointer Mastery](./41-pointer-mastery.md) (Manual pointers via `ctypes`)

### Low-Level Concurrency
- [Process Forking](./concurrency/01-forking.md) (`multiprocessing`)
- [Multi-Threading](./concurrency/02-threads.md) (Threads)

### Low-Level Networking
- [Socket Basics](./network/01-sockets.md) (`socket` module)
- [Protocols: TCP & UDP](./network/02-protocols.md) (Streams vs Datagrams)

### Toolchain Lifecycle
- [Linking & Delivery](./build/02-linking.md) (PyInstaller, Wheels)
