# 🏛️ [Master Pwsh Reference (One-Shot)](master-pwsh.md)

# 🧭 Pwsh Language Blueprint: Tiered Learning (v2)

This roadmap groups the 53 universal language topics by **Mastery Tier**, covering both Windows PowerShell 5.1 and modern PowerShell 7+.

---

## 🟢 Tier 1: The Foundation [CORE]
*The non-skippable essentials.*

### Environment & Setup
- [01-toolchain-installation.md](./setup/01-toolchain-installation.md)
- [02-compilation-run-basics.md](./setup/02-compilation-run-basics.md)

### Lexical & Data
- [03-tokens-lexemes.md](./04-tokens-lexemes.md)
- [04-keywords-standards.md](./05-keywords-standards.md)
- [05-comments-metadata.md](./07-comments-metadata.md)
- [06-variables-constants.md](./08-variables-constants.md)
- [07-data-types.md](./09-data-types.md) (Hub)
- [08-string-escaping.md](./10-string-escaping.md)
- [09-interpolation.md](./11-interpolation.md)
- [10-scope-lifetime.md](./12-scope-lifetime.md)

### Logic & Control
- [11-operators.md](./17-operators.md) (Hub)
- [12-precedence-associativity.md](./18-precedence-associativity.md)
- [13-expressions-statements.md](./19-expressions-statements.md)
- [14-type-casting.md](./21-type-casting.md)
- [15-truth-rule.md](./22-truth-rule.md)
- [16-conditionals.md](./23-conditionals.md) (Hub)
- [17-iteration-definite.md](./24-iteration-definite.md)
- [18-iteration-indefinite.md](./25-iteration-indefinite.md)

### The Function Engine
- [19-function-basics.md](./27-function-basics.md)
- [20-return-types.md](./28-return-types.md)
- [21-recursion.md](./29-recursion.md)
- [22-passing-mechanisms.md](./30-passing-mechanisms.md)

### Architecture & Environment
- [23-sequential-collections.md](./32-sequential-collections.md) (Hub)
    - [array-lists.md](array-lists.md)
- [24-associative-collections.md](./33-associative-collections.md)
- [25-structs-base.md](./34-structs-base.md)
- [26-class-concept.md](./36-class-concept.md)
- [27-io-streams.md](./45-io-streams.md)
- [28-error-handling.md](./49-error-handling.md)

---

## 🔵 Tier 2: Idiomatic Power [PRO]
*Native techniques and efficiency.*

### Efficiency & Native Power
- [29-tuning-strictness.md](./06-tuning-strictness.md)
- [30-native-strings.md](./14-native-strings.md)
- [31-pattern-matching.md](./15-pattern-matching.md)
- [32-command-substitution.md](./20-command-substitution.md)
- [33-jump-statements.md](./26-jump-statements.md)
- [34-closures-lambdas.md](./31-closures-lambdas.md)

### Advanced Redirections
- [35-procedural-mechanisms.md](./procedural/35-procedural-mechanisms.md) (Conceptual Hub)
    - [Modules](./procedural/modules.md)
    - [Dot-Sourcing](dot-sourcing.md)
- [36-advanced-oop.md](./oop/37-advanced-oop.md) (Conceptual Hub)
    - [Encapsulation](./oop/encapsulation.md)
    - [Inheritance](./oop/inheritance.md)
    - [Polymorphism](./oop/polymorphism.md)
    - [Abstraction](./oop/abstraction.md)
- [37-async-coroutines.md](./40-async-coroutines.md)
- [38-http-client-api.md](./network/44-http-client-api.md)
- [39-redirection-piping.md](./46-redirection-piping.md)

### Project Lifecycle & Build
- [40-multi-file-projects.md](./build/50-multi-file-projects.md)
- [41-build-tools.md](./build/51-build-tools.md)
- [42-standard-library.md](./53-standard-library.md)

---

## 🔴 Tier 3: Advanced Internals [SYSTEMS]
*The engine and the OS.*

### Internals & Memory
- [43-charset.md](./03-charset.md)
- [44-storage-classes.md](./13-storage-classes.md)
- [45-syntactic-automation.md](./16-syntactic-automation.md)
- [46-synchronization-locks.md](./concurrency/41-synchronization-locks.md)
- [47-exit-codes-signals.md](./47-exit-codes-signals.md)
- [48-memory-management.md](./48-memory-management.md)
- [49-pointer-mastery.md](./41-pointer-mastery.md)

### Low-Level Concurrency
- [50-process-forking.md](./concurrency/38-process-forking.md)
- [51-multi-threading.md](./concurrency/39-multi-threading.md)

### Low-Level Networking
- [52-socket-basics.md](./42-socket-basics.md)
- [53-tcp-udp-patterns.md](./43-tcp-udp-patterns.md)
