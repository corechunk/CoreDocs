# 🧭 Bash Wiki: The Full Picture

This is the **Chronological Path**. Topics are ordered by the natural learning progression, with status tags to indicate their level.

---

## 🗺️ The Roadmap

### Phase 1: Environment & Setup
1. [01-toolchain-installation.md](./setup/01-toolchain-installation.md) **[CORE]** (OS-specific setup, `mise`, PATH)
2. [02-compilation-run-basics.md](./setup/02-compilation-run-basics.md) **[CORE]** (Execution ritual, Shebangs)

### Phase 2: Lexical Foundations
3. [03-charset.md](./03-charset.md) **[SYSTEMS]** (UTF-8, Locale, LANG)
4. [04-tokens-lexemes.md](./04-tokens-lexemes.md) **[CORE]** (Atoms of the language, Whitespace)
5. [05-keywords-standards.md](./05-keywords-standards.md) **[CORE]** (Keywords vs Built-ins vs Externals)
6. [06-tuning-strictness.md](./06-tuning-strictness.md) **[PRO]** (Safe Mode: `set -euo pipefail`)
7. [07-comments-metadata.md](./07-comments-metadata.md) **[CORE]** (Doc-strings, Metadata)

### Phase 3: Primitive Data
8. [08-variables-constants.md](./08-variables-constants.md) **[CORE]** (Declaration, `readonly`)
9. [09-data-types.md](./09-data-types.md) **[CORE]** (String model, `declare -i`)
    - [Parameter Expansion](./data-type/parameter-expansion.md)
    - [Null Safety & Defaults](./data-type/null-safety.md)
    - [Floating Point Limits](./data-type/floating-point.md)
10. [10-string-escaping.md](./10-string-escaping.md) **[CORE]** (Escape sequences, `echo -e`)
11. [11-interpolation.md](./11-interpolation.md) **[CORE]** (Variable Substitution, Defaults)
12. [12-scope-lifetime.md](./12-scope-lifetime.md) **[CORE]** (`local`, `export`, Subshells)
13. [13-storage-classes.md](./13-storage-classes.md) **[SYSTEMS]** (Env variables, Static simulation)

### Phase 4: Native Power (Efficiency)
14. [14-native-strings.md](./14-native-strings.md) **[PRO]** (Parameter Expansion, Slicing)
15. [15-pattern-matching.md](./15-pattern-matching.md) **[PRO]** (Globbing, Regex `=~`)
16. [16-syntactic-automation.md](./16-syntactic-automation.md) **[SYSTEMS]** (Aliases, Functions)

### Phase 5: Operations & Logic
17. [17-operators.md](./17-operators.md) **[CORE]** (Math, Logic, Bitwise)
    - [Bitwise Operators](./operator/bitwise.md)
18. [18-precedence-associativity.md](./18-precedence-associativity.md) **[CORE]** (Order of operations)
19. [19-expressions-statements.md](./19-expressions-statements.md) **[CORE]** (Exit statuses)
20. [20-command-substitution.md](./20-command-substitution.md) **[PRO]** (Capturing output `$( )`)
21. [21-type-casting.md](./21-type-casting.md) **[CORE]** (Contextual interpretation)

### Phase 6: Control Flow
22. [22-truth-rule.md](./22-truth-rule.md) **[CORE]** (0 = Success)
23. [23-conditionals.md](./23-conditionals.md) **[CORE]** (`if`, `case`)
24. [24-iteration-definite.md](./24-iteration-definite.md) **[CORE]** (`for` loops)
25. [25-iteration-indefinite.md](./25-iteration-indefinite.md) **[CORE]** (`while`, `until`)
26. [26-jump-statements.md](./26-jump-statements.md) **[PRO]** (`break`, `continue`, `exit`)

### Phase 7: The Function Engine
27. [27-function-basics.md](./27-function-basics.md) **[CORE]** (Declaration, `local`)
    - [Argument Array ($@)](./array/expansion-manipulation.md)
28. [28-return-types.md](./28-return-types.md) **[CORE]** (Exit status, capturing stdout)
29. [29-recursion.md](./29-recursion.md) **[CORE]** (Call limits, `BASHPID`)
30. [30-passing-mechanisms.md](./30-passing-mechanisms.md) **[CORE]** (Positional parameters, `nameref`)
31. [31-closures-lambdas.md](./31-closures-lambdas.md) **[PRO]** (Dynamic function simulation)

### Phase 8: Procedural Architecture
32. [32-sequential-collections.md](./32-sequential-collections.md) **[CORE]** (Indexed Arrays)
    - [Expansion & Manipulation](./array/expansion-manipulation.md)
33. [33-associative-collections.md](./33-associative-collections.md) **[CORE]** (Hashmaps `declare -A`)
34. [34-structs-base.md](./34-structs-base.md) **[CORE]** (Simulated via Associative Arrays)
35. [35-procedural-mechanisms.md](./procedural/35-procedural-mechanisms.md) **[PRO]** (Modular scripts, `source`)

### Phase 9: Object-Oriented Programming
36. [36-class-concept.md](./36-class-concept.md) **[CORE]** (Namerefs + Associative Arrays)
37. [37-advanced-oop.md](./oop/37-advanced-oop.md) **[PRO]** (Encapsulation, Dynamic Dispatch)

### Phase 10: Concurrency & Async
38. [38-process-forking.md](./concurrency/38-process-forking.md) **[SYSTEMS]** (Backgrounding `&`, `wait`)
39. [39-multi-threading.md](./concurrency/39-multi-threading.md) **[SYSTEMS]** (GNU Parallel, Background jobs)
40. [40-async-coroutines.md](./concurrency/40-async-coroutines.md) **[PRO]** (`coproc`)
41. [41-synchronization-locks.md](./concurrency/41-synchronization-locks.md) **[SYSTEMS]** (`flock`, Lock files)

### Phase 11: Network Handling
42. [42-socket-basics.md](./network/42-socket-basics.md) **[SYSTEMS]** (`/dev/tcp`, `/dev/udp`)
43. [43-tcp-udp-patterns.md](./network/43-tcp-udp-patterns.md) **[SYSTEMS]** (Raw streams)
44. [44-http-client-api.md](./network/44-http-client-api.md) **[PRO]** (`curl`, `wget`)

### Phase 12: OS Bridge & Memory
45. [45-io-streams.md](./45-io-streams.md) **[CORE]** (0, 1, 2)
46. [46-redirection-piping.md](./46-redirection-piping.md) **[PRO]** (Redirection, Pipes, Heredocs)
47. [47-exit-codes-signals.md](./47-exit-codes-signals.md) **[SYSTEMS]** (`trap`, `kill`, SIGINT)
48. [48-memory-management.md](./memory/48-memory-management.md) **[SYSTEMS]** (`unset`, Ramdisk logic)
49. [49-error-handling.md](./49-error-handling.md) **[CORE]** (`trap ERR`, `set -e`)

### Phase 13: Project Lifecycle & Build
50. [50-multi-file-projects.md](./build/50-multi-file-projects.md) **[PRO]** (Source orchestration)
51. [51-build-tools.md](./build/51-build-tools.md) **[PRO]** (Shellcheck, `install`)
52. [52-linking-delivery.md](./build/52-linking-delivery.md) **[SYSTEMS]** (Self-contained scripts)
53. [53-standard-library.md](./build/53-standard-library.md) **[PRO]** (Coreutils, Built-ins)


---

## 🏷️ Tier Definitions
- **[CORE]**: Fundamental logic. Essential for beginners.
- **[PRO]**: Native power and idiomatic efficiency.
- **[SYSTEMS]**: Low-level internals and OS integration.
