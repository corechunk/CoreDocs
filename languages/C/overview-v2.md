<!--
PROMPT CONTEXT:
"so now we will make c wiki with legacy aware annotation for what we would do in legacy code in another code snippet like having to add header for bool also 

thats it but before making the wiki i want you to read the whole pseudo-language/ folder and all files in it thoroughly. then ull confirm and present what u understood then ill permit to procceed"

"also u must make v1 and v2 file like

overview.md and overview-v2.md then after making all the 53 files u have to make a master-c.md with master blueprint

and those 53 files, some of them are core pro and sytem each will follow their own blueprints. also i dont have to remind you that u must use code snippets. dont try to glove every topic in one file to be globed in one code box but for saperate things or saperate implimentation in a file use another saperate code box.
-->

# 🏛️ [Master C Reference (One-Shot)](master-c.md)

# 🧭 C Language Blueprint: Tiered Learning (v2)

This roadmap groups the 53 universal C topics by **Mastery Tier**. Numbering inside `[]` restarts from 01 in each category.

---

## 🟢 Tier 1: The Foundation [CORE]
*The non-skippable essentials. Master these to write functional, correct code.*

### Environment & Setup
- [01-toolchain-installation.md](./setup/01-toolchain-installation.md)
- [02-compilation-run-basics.md](./setup/02-compilation-run-basics.md)

### Lexical & Data
- [01-tokens-lexemes.md](./04-tokens-lexemes.md)
- [02-keywords-standards.md](./05-keywords-standards.md)
- [03-comments-metadata.md](./07-comments-metadata.md)
- [04-variables-constants.md](./08-variables-constants.md)
- [05-data-types.md](./09-data-types.md) (Conceptual Hub)
    - [integers.md](./data-type/integers.md)
    - [floats.md](./data-type/floats.md)
    - [fixed-width.md](./data-type/fixed-width.md)
    - [special-types.md](./data-type/special-types.md)
- [06-string-escaping.md](./10-string-escaping.md)
- [07-interpolation.md](./11-interpolation.md)
- [08-scope-lifetime.md](./12-scope-lifetime.md)

### Logic & Control
- [01-operators.md](./17-operators.md) (Conceptual Hub)
    - [math.md](./operator/math.md)
    - [logical.md](./operator/logical.md)
    - [bitwise.md](./operator/bitwise.md)
    - [assignment.md](./operator/assignment.md)
- [02-precedence-associativity.md](./18-precedence-associativity.md)
- [03-expressions-statements.md](./19-expressions-statements.md)
- [04-type-casting.md](./21-type-casting.md)
- [05-truth-rule.md](./22-truth-rule.md)
- [06-conditionals.md](./23-conditionals.md) (Conceptual Hub)
    - [if-else.md](./control/if-else.md)
    - [switch.md](./control/switch.md)
- [07-iteration-definite.md](./24-iteration-definite.md)
- [08-iteration-indefinite.md](./25-iteration-indefinite.md)

### The Function Engine
- [01-function-basics.md](./27-function-basics.md)
- [02-return-types.md](./28-return-types.md)
- [03-recursion.md](./29-recursion.md)
- [04-passing-mechanisms.md](./30-passing-mechanisms.md)

### Architecture & Environment
- [01-sequential-collections.md](./32-sequential-collections.md) (Conceptual Hub)
    - [fixed.md](./array/fixed.md)
    - [vla.md](./array/vla.md)
    - [multidim.md](./array/multidim.md)
- [02-associative-collections.md](./33-associative-collections.md)
- [03-structs-base.md](./34-structs-base.md)
    - [Procedural Mechanisms](./procedural/35-procedural-mechanisms.md)
- [04-class-concept.md](./36-class-concept.md)
    - [Advanced OOP](./oop/37-advanced-oop.md)
- [05-io-streams.md](./45-io-streams.md)
- [06-error-handling.md](./49-error-handling.md)

---

## 🔵 Tier 2: Idiomatic Power [PRO]
*Native techniques and efficiency. Master these to write "Professional" code.*

### Efficiency & Native Power
- [01-tuning-strictness.md](./06-tuning-strictness.md)
- [02-native-strings.md](./14-native-strings.md)
- [03-pattern-matching.md](./15-pattern-matching.md)
- [04-command-substitution.md](./20-command-substitution.md)
- [05-jump-statements.md](./26-jump-statements.md)
- [06-closures-lambdas.md](./31-closures-lambdas.md)

### Advanced Redirections & OOP
- [01-procedural-mechanisms.md](./procedural/35-procedural-mechanisms.md) (Hub)
    - [Static & Linkage](./procedural/static-linkage.md)
    - [Header Architecture](./procedural/headers.md)
- [02-advanced-oop.md](./oop/37-advanced-oop.md)
- [03-async-coroutines.md](./concurrency/40-async-coroutines.md)
- [04-http-client-api.md](./network/44-http-client-api.md)
- [05-redirection-piping.md](./46-redirection-piping.md)

### Project Lifecycle & Build
- [01-multi-file-projects.md](./build/50-multi-file-projects.md)
- [02-build-tools.md](./build/51-build-tools.md)
- [03-standard-library.md](./53-standard-library.md)

---

## 🔴 Tier 3: Advanced Internals [SYSTEMS]
*The engine and the OS. Master these to build systems, compilers, or drivers.*

### Internals & Memory
- [01-charset.md](./03-charset.md)
- [02-storage-classes.md](./13-storage-classes.md)
- [03-syntactic-automation.md](./16-syntactic-automation.md)
- [04-synchronization-locks.md](./concurrency/41-synchronization-locks.md)
- [05-exit-codes-signals.md](./47-exit-codes-signals.md)
- [06-memory-management.md](./memory/48-memory-management.md) (Conceptual Hub)
    - [stack-heap.md](./memory/stack-heap.md)
    - [allocation.md](./memory/allocation.md)
    - [pointer-arithmetic.md](./memory/pointer-arithmetic.md)

### Low-Level Concurrency & Networking
- [01-process-forking.md](./concurrency/38-process-forking.md) (Conceptual Hub)
    - [fork.md](./concurrency/fork.md)
    - [exec.md](./concurrency/exec.md)
- [02-multi-threading.md](./concurrency/39-multi-threading.md)
- [03-socket-basics.md](./network/42-socket-basics.md) (Conceptual Hub)
    - [listen.md](./network/listen.md)
    - [connect.md](./network/connect.md)
- [04-tcp-udp-patterns.md](./network/43-tcp-udp-patterns.md)

### Toolchain Lifecycle
- [01-linking-delivery.md](./build/52-linking-delivery.md)
