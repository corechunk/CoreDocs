# 🧭 Bash Wiki: Tiered Learning (v2)

This roadmap groups the 53 universal language topics by **Mastery Tier**. Use this to focus on the Foundation, Idiomatic Power, or Systems Internals.

---

## 🟢 Tier 1: The Foundation [CORE]
*The non-skippable essentials. Master these to write functional, correct code.*

### Environment & Setup
- [01-toolchain-installation.md](./setup/01-toolchain-installation.md) (Installation, `mise`, PATH)
- [02-compilation-run-basics.md](./setup/02-compilation-run-basics.md) (Execution ritual, Shebangs)

### Lexical & Data
- [04-tokens-lexemes.md](./04-tokens-lexemes.md) (Atoms of the language, Whitespace)
- [05-keywords-standards.md](./05-keywords-standards.md) (Keywords vs Built-ins)
- [07-comments-metadata.md](./07-comments-metadata.md) (Doc-strings, Metadata)
- [08-variables-constants.md](./08-variables-constants.md) (Declaration, `readonly`)
- [09-data-types.md](./09-data-types.md) (String model, `declare -i`)
    - [Parameter Expansion](./data-type/parameter-expansion.md)
    - [Null Safety & Defaults](./data-type/null-safety.md)
    - [Floating Point Limits](./data-type/floating-point.md)
- [10-string-escaping.md](./10-string-escaping.md)
- [11-interpolation.md](./11-interpolation.md) (Variable Substitution)
- [12-scope-lifetime.md](./12-scope-lifetime.md) (Global, `local`)

### Logic & Control
- [17-operators.md](./17-operators.md)
    - [Bitwise Operators](./operator/bitwise.md)
- [18-precedence-associativity.md](./18-precedence-associativity.md)
- [19-expressions-statements.md](./19-expressions-statements.md) (Exit statuses)
- [21-type-casting.md](./21-type-casting.md) (Contextual evaluation)
- [22-truth-rule.md](./22-truth-rule.md) (0 = Success)
- [23-conditionals.md](./23-conditionals.md) (`if`, `case`)
- [24-iteration-definite.md](./24-iteration-definite.md) (For loops)
- [25-iteration-indefinite.md](./25-iteration-indefinite.md) (While, Until)

### The Function Engine
- [27-function-basics.md](./27-function-basics.md)
    - [Argument Array ($@)](./array/expansion-manipulation.md)
- [28-return-types.md](./28-return-types.md) (Exit codes, Stdout)
- [29-recursion.md](./29-recursion.md)
- [30-passing-mechanisms.md](./30-passing-mechanisms.md) (Positional params, Namerefs)

### Architecture & Environment
- [32-sequential-collections.md](./32-sequential-collections.md) (Indexed Arrays)
    - [Expansion & Manipulation](./array/expansion-manipulation.md)
- [33-associative-collections.md](./33-associative-collections.md) (Hashmaps)

- [34-structs-base.md](./34-structs-base.md) (Simulated via Associative Arrays)
- [36-class-concept.md](./36-class-concept.md) (Namerefs + Associative Arrays)
- [45-io-streams.md](./45-io-streams.md) (0, 1, 2)
- [49-error-handling.md](./49-error-handling.md) (`set -e`, `trap ERR`)

---

## 🔵 Tier 2: Idiomatic Power [PRO]
*Native techniques and efficiency. Master these to write "Professional" code.*

### Efficiency & Native Power
- [06-tuning-strictness.md](./06-tuning-strictness.md) (Safe Mode flags)
- [14-native-strings.md](./14-native-strings.md) (Parameter Expansion slicing)
- [15-pattern-matching.md](./15-pattern-matching.md) (Regex, Globbing)
- [20-command-substitution.md](./20-command-substitution.md) (`$( )`)
- [26-jump-statements.md](./26-jump-statements.md) (Break, Continue)
- [31-closures-lambdas.md](./31-closures-lambdas.md)

### Advanced Redirections
- [35-procedural-mechanisms.md](./procedural/35-procedural-mechanisms.md) **[START FILE]**
    - Modular scripts, `source`.
- [37-advanced-oop.md](./oop/37-advanced-oop.md) **[START FILE]**
    - Encapsulation, Dynamic Dispatch.
- [40-async-coroutines.md](./concurrency/40-async-coroutines.md) (`coproc`)
- [44-http-client-api.md](./network/44-http-client-api.md) (`curl`, `wget`)
- [46-redirection-piping.md](./46-redirection-piping.md) (Pipes, Heredocs)

### Project Lifecycle & Build
- [50-multi-file-projects.md](./build/50-multi-file-projects.md)
- [51-build-tools.md](./build/51-build-tools.md) (Shellcheck)
- [53-standard-library.md](./build/53-standard-library.md) (Coreutils)

---

## 🔴 Tier 3: Advanced Internals [SYSTEMS]
*The engine and the OS. Master these to build systems, compilers, or drivers.*

### Internals & Memory
- [03-charset.md](./03-charset.md) (UTF-8, Locale)
- [13-storage-classes.md](./13-storage-classes.md) (Env variables)
- [16-syntactic-automation.md](./16-syntactic-automation.md) (Aliases)
- [48-memory-management.md](./memory/48-memory-management.md) **[START FILE]**
    - Unset, Ramdisk logic.
- [05-pointer-mastery.md](./30-passing-mechanisms.md) (Namerefs / `declare -n`)
- [47-exit-codes-signals.md](./47-exit-codes-signals.md) (`trap`, `kill`)

### Low-Level Concurrency
- [38-process-forking.md](./concurrency/38-process-forking.md) (Backgrounding)
- [39-multi-threading.md](./concurrency/39-multi-threading.md) (GNU Parallel)
- [41-synchronization-locks.md](./concurrency/41-synchronization-locks.md) (`flock`)

### Low-Level Networking
- [42-socket-basics.md](./network/42-socket-basics.md) (`/dev/tcp`)
- [43-tcp-udp-patterns.md](./network/43-tcp-udp-patterns.md) (Raw streams)

### Toolchain Lifecycle
- [52-linking-delivery.md](./build/52-linking-delivery.md)
    - Self-contained scripts.
