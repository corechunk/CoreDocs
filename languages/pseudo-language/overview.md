# 🏛️ [Master <Language> Reference (One-Shot)](./master-<language_name>.md)

# 🧭 Universal Language Blueprint: The Full Picture

This is the **Chronological Path**. Topics are ordered by the natural learning progression, with status tags to indicate their level.

---

## 🗺️ The Roadmap

### Phase 1: Environment & Setup
1. [01-toolchain-installation.md](./setup/00-start.md) **[CORE]** (OS-specific setup, `mise`, PATH)
2. [02-compilation-run-basics.md](./setup/01-compile-run.md) **[CORE]** (Execution ritual, Hello World)

### Phase 2: Lexical Foundations
3. [03-charset.md](./03-charset.md) **[SYSTEMS]** (ASCII, UTF-8, Unicode)
4. [04-tokens-lexemes.md](./04-tokens-lexemes.md) **[CORE]** (Atoms of the language)
5. [05-keywords-standards.md](./05-keywords-standards.md) **[CORE]** (Evolution & Standards)
6. [06-tuning-strictness.md](./06-tuning-strictness.md) **[PRO]** (POSIX, C-Strict, Compiler flags)
7. [07-comments-metadata.md](./07-comments-metadata.md) **[CORE]** (Doc-strings, Shebangs)

### Phase 3: Primitive Data
8. [08-variables-constants.md](./08-variables-constants.md) **[CORE]** (Declaration, Definition)
9. [09-data-types.md](./09-data-types.md) **[CORE]** (Conceptual Hub)
    - [integers.md](./data-type/integers.md)
    - [floats.md](./data-type/floats.md)
    - [fixed-width.md](./data-type/fixed-width.md)
    - [special-types.md](./data-type/special-types.md)
10. [10-string-escaping.md](./10-string-escaping.md) **[CORE]** (Invisible/Illegal characters)
11. [11-interpolation.md](./11-interpolation.md) **[CORE]** (Variable Substitution)
12. [12-scope-lifetime.md](./12-scope-lifetime.md) **[CORE]** (RAII, Namespaces)
13. [13-storage-classes.md](./13-storage-classes.md) **[SYSTEMS]** (Static, Extern, Volatile, Register)

### Phase 4: Native Power (Efficiency)
14. [14-native-strings.md](./14-native-strings.md) **[PRO]** (Built-in Slicing/Parsing)
15. [15-pattern-matching.md](./15-pattern-matching.md) **[PRO]** (Globbing, Regex)
16. [16-syntactic-automation.md](./16-syntactic-automation.md) **[SYSTEMS]** (Templates, Concepts, Type-traits)

### Phase 5: Operations & Logic
17. [17-operators.md](./17-operators.md) **[CORE]** (Math, Logic, Bitwise Hub)
    - [math.md](./operator/math.md)
    - [bitwise.md](./operator/bitwise.md)
18. [18-precedence-associativity.md](./18-precedence-associativity.md) **[CORE]** (Order of operations)
19. [19-expressions-statements.md](./19-expressions-statements.md) **[CORE]** (Values vs. Actions)
20. [20-command-substitution.md](./20-command-substitution.md) **[PRO]** (Capturing output)
21. [21-type-casting.md](./21-type-casting.md) **[CORE]** (Implicit vs. Explicit)

### Phase 6: Control Flow
22. [22-truth-rule.md](./22-truth-rule.md) **[CORE]** (Definition of Truth/Zero-parity)
23. [23-conditionals.md](./22-conditionals.md) **[CORE]** (if, else, switch Hub)
    - [if.md](./control/if.md)
    - [switch.md](./control/switch.md)
24. [24-iteration-definite.md](./23-iteration-definite.md) **[CORE]** (For loops)
25. [25-iteration-indefinite.md](./24-iteration-indefinite.md) **[CORE]** (While, Repeat)
26. [26-jump-statements.md](./25-jump-statements.md) **[PRO]** (Break, Continue, Goto)

### Phase 7: The Function Engine
27. [27-function-basics.md](./26-function-basics.md) **[CORE]**
28. [28-return-types.md](./27-return-types.md) **[CORE]**
29. [29-recursion.md](./28-recursion.md) **[CORE]** (Call Stack visuals)
30. [30-passing-mechanisms.md](./29-passing-mechanisms.md) **[CORE]** (Value vs Ptr vs Ref)

## Functional Paradigm [optional] [PRO]
31. [31-closures-lambdas.md](./30-closures-lambdas.md) (Anonymous functions)
32. [32-higher-order.md](./31-higher-order.md)
33. [33-pure-functions.md](./32-pure.md)
34. [34-currying.md](./33-currying.md)

### Phase 8: Procedural Architecture
35. [35-sequential-collections.md](./31-sequential-collections.md) **[CORE]** (Hub)
    - [fixed.md](./array/fixed.md)
    - [lists.md](./array/lists.md)
36. [36-associative-collections.md](./32-associative-collections.md) **[CORE]** (Maps, Sets)
37. [37-structs-base.md](./33-structs-base.md) **[CORE]** (Gateway to Procedural Hub)
38. [38-procedural-mechanisms.md](./procedural/00-start.md) **[PRO]** (Hub)
    - [Namespaces-Modules](./procedural/modules.md)
    - [Top-Level-Execution](./procedural/top-level.md)

### Phase 9: Object-Oriented Programming
39. [39-class-concept.md](./35-class-concept.md) **[CORE]** (Gateway to OOP Hub)
40. [40-advanced-oop.md](./oop/00-start.md) **[PRO]** (Hub)
    - [Encapsulation](./oop/encapsulation.md)
    - [Inheritance](./oop/inheritance.md)
    - [Polymorphism](./oop/polymorphism.md)
    - [Abstraction](./oop/abstraction.md)

### Phase 10: Concurrency & Async
41. [41-process-forking.md](./concurrency/01-forking.md) **[SYSTEMS]** (Process vs. Thread)
42. [42-multi-threading.md](./concurrency/02-threads.md) **[SYSTEMS]** (pthreads, concurrency)
43. [43-async-coroutines.md](./concurrency/03-async.md) **[PRO]** (Non-blocking I/O)
44. [44-synchronization-locks.md](./concurrency/04-sync.md) **[SYSTEMS]** (Race conditions, Mutex)

### Phase 11: Network Handling
45. [45-socket-basics.md](./network/01-sockets.md) **[SYSTEMS]** (IP/Ports, Listen/Connect)
46. [46-tcp-udp-patterns.md](./network/02-protocols.md) **[SYSTEMS]** (Streams vs. Datagrams)
47. [47-http-client-api.md](./network/03-http.md) **[PRO]** (Web communication)

### Phase 12: OS Bridge & Memory
48. [48-io-streams.md](./37-io-streams.md) **[CORE]** (stdin, stdout, stderr)
49. [49-redirection-piping.md](./38-redirection-piping.md) **[PRO]** (Glue logic)
50. [50-exit-codes-signals.md](./39-exit-codes-signals.md) **[SYSTEMS]** (Process termination, SIGINT)
51. [51-memory-management.md](./memory/00-start.md) **[SYSTEMS]** (Hub)
    - [stack-heap.md](./memory/stack-heap.md)
    - [allocation.md](./memory/allocation.md)
52. [52-error-handling.md](./42-error-handling.md) **[CORE]** (Result types, errno, Exceptions)

### Phase 13: Project Lifecycle & Build
53. [53-multi-file-projects.md](./build/00-start.md) **[PRO]**
54. [54-build-tools.md](./build/01-tools.md) **[PRO]**
55. [55-linking-delivery.md](./build/02-linking.md) **[SYSTEMS]**
56. [56-standard-library.md](./45-standard-library.md) **[PRO]** (Core utility list)


---

## 🏷️ Tier Definitions
- **[CORE]**: Fundamental logic. Essential for beginners.
- **[PRO]**: Native power and idiomatic efficiency.
- **[SYSTEMS]**: Low-level internals and OS integration.
