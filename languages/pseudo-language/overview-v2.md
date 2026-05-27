# 🏛️ [Master <Language> Reference (One-Shot)](./master-<language_name>.md)

# 🧭 Universal Language Blueprint: Tiered Learning (v2)

This roadmap groups the 53 universal language topics by **Mastery Tier**. Numbering inside `[]` restarts from 01 in each category.

---

## 🟢 Tier 1: The Foundation [CORE]
*The non-skippable essentials. Master these to write functional, correct code.*

### Environment & Setup
- [01-toolchain-installation.md](./setup/00-start.md) (Installation, `mise`, PATH)
- [02-compilation-run-basics.md](./setup/01-compile-run.md) (Execution ritual, Hello World)

### Lexical & Data
- [01-tokens-lexemes.md](./04-tokens-lexemes.md) (Atoms of the language)
- [02-keywords-standards.md](./05-keywords-standards.md) (Evolution & Standards)
- [03-comments-metadata.md](./07-comments-metadata.md) (Doc-strings, Shebangs)
- [04-variables-constants.md](./08-variables-constants.md)
- [05-data-types.md](./09-data-types.md) (Conceptual Hub)
    - [integers.md](./data-type/integers.md)
    - [floats.md](./data-type/floats.md)
    - [fixed-width.md](./data-type/fixed-width.md)
    - [special-types.md](./data-type/special-types.md)
- [06-string-escaping.md](./10-string-escaping.md)
- [07-interpolation.md](./11-interpolation.md) (Variable Substitution)
- [08-scope-lifetime.md](./12-scope-lifetime.md) (Shadowing, Visibility)

### Logic & Control
- [01-operators.md](./17-operators.md) (Conceptual Hub)
    - [math.md](./operator/math.md)
    - [bitwise.md](./operator/bitwise.md)
- [02-precedence-associativity.md](./18-precedence-associativity.md)
- [03-expressions-statements.md](./19-expressions-statements.md)
- [04-type-casting.md](./21-type-casting.md)
- [05-truth-rule.md](./22-truth-rule.md) (Truthiness/Zero-parity)
- [06-conditionals.md](./22-conditionals.md) (Conceptual Hub)
    - [if.md](./control/if.md)
    - [switch.md](./control/switch.md)
- [07-iteration-definite.md](./23-iteration-definite.md) (For loops)
- [08-iteration-indefinite.md](./24-iteration-indefinite.md) (While, Repeat)

### The Function Engine
- [01-function-basics.md](./26-function-basics.md) (Declaration, Blocks)
- [02-return-types.md](./27-return-types.md) (Void, early returns)
- [03-recursion.md](./28-recursion.md) (Call Stack visuals)
- [04-passing-mechanisms.md](./29-passing-mechanisms.md) (Value vs Ptr vs Ref)

## Functional Paradigm [optional] [PRO]
*For languages supporting FP (Kotlin, Lua, Python, etc.)*
- [01-closures-lambdas.md](./30-closures-lambdas.md) (Anonymous functions)
- [02-higher-order-functions.md](./31-higher-order.md)
- [03-immutability-pure-functions.md](./32-pure.md)
- [04-currying-partial-application.md](./33-currying.md)

### Architecture & Environment
- [01-sequential-collections.md](./31-sequential-collections.md) (Conceptual Hub)
    - [fixed.md](./array/fixed.md)
    - [lists.md](./array/lists.md)
- [02-associative-collections.md](./32-associative-collections.md) (Maps, Sets)
- [03-structs-base.md](./33-structs-base.md) (Gateway to Procedural Hub)
- [04-class-concept.md](./35-class-concept.md) (Gateway to OOP Hub)
- [05-io-streams.md](./37-io-streams.md) (stdin, stdout, stderr)
- [06-error-handling.md](./42-error-handling.md) (Result types, errno, Exceptions)

---

## 🔵 Tier 2: Idiomatic Power [PRO]
*Native techniques and efficiency. Master these to write "Professional" code.*

### Efficiency & Native Power
- [01-tuning-strictness.md](./06-tuning-strictness.md) (POSIX, C-Strict, Flags)
- [02-native-strings.md](./14-native-strings.md) (Built-in Slicing/Parsing)
- [03-pattern-matching.md](./15-pattern-matching.md) (Globbing, Regex)
- [04-command-substitution.md](./20-command-substitution.md)
- [05-jump-statements.md](./25-jump-statements.md) (Break, Continue, Goto)

### Advanced Redirections
- [01-procedural-mechanisms.md](./procedural/00-start.md) (Conceptual Hub)
    - [Namespaces-Modules](./procedural/modules.md)
    - [Top-Level-Execution](./procedural/top-level.md)
- [02-advanced-oop.md](./oop/00-start.md) (Conceptual Hub)
    - [Encapsulation](./oop/encapsulation.md)
    - [Inheritance](./oop/inheritance.md)
    - [Polymorphism](./oop/polymorphism.md)
    - [Abstraction](./oop/abstraction.md)
- [03-async-coroutines.md](./concurrency/03-async.md) (Non-blocking I/O)
- [04-http-client-api.md](./network/03-http.md) (Web communication)
- [05-redirection-piping.md](./38-redirection-piping.md) (Glue logic)

### Project Lifecycle & Build
- [01-multi-file-projects.md](./build/00-start.md)
- [02-build-tools.md](./build/01-tools.md)
- [03-standard-library.md](./45-standard-library.md) (Core utility list)

---

## 🔴 Tier 3: Advanced Internals [SYSTEMS]
*The engine and the OS. Master these to build systems, compilers, or drivers.*

### Internals & Memory
- [01-charset.md](./03-charset.md) (ASCII, UTF-8, Unicode)
- [02-storage-classes.md](./13-storage-classes.md) (Static, Extern, Volatile, Register)
- [03-syntactic-automation.md](./16-syntactic-automation.md) (Macros, Auto-gen, Data Classes)
- [04-synchronization-locks.md](./concurrency/04-sync.md) (Race conditions, Mutex)
- [05-exit-codes-signals.md](./39-exit-codes-signals.md) (Process termination, SIGINT)
- [06-memory-management.md](./memory/00-start.md) (Conceptual Hub)
    - [stack-heap.md](./memory/stack-heap.md)
    - [allocation.md](./memory/allocation.md)
- [07-pointer-mastery.md](./41-pointer-mastery.md) (Advanced Addressing)

### Low-Level Concurrency
- [01-process-forking.md](./concurrency/01-forking.md) (Conceptual Hub)
    - [fork.md](./concurrency/fork.md)
    - [exec.md](./concurrency/exec.md)
- [02-multi-threading.md](./concurrency/02-threads.md) (pthreads, shared state)

### Low-Level Networking
- [01-socket-basics.md](./network/01-sockets.md) (Conceptual Hub)
    - [listen.md](./network/listen.md)
    - [connect.md](./network/connect.md)
- [02-tcp-udp-patterns.md](./network/02-protocols.md) (Streams vs. Datagrams)

### Toolchain Lifecycle
- [01-linking-delivery.md](./build/02-linking.md)
    - Static vs. Dynamic linking internals.
