# 🔤 Comprehensive Introduction to Assembly Language & Instruction Set Architectures

This master guide serves as a comprehensive reference for learning assembly language across the three primary modern CPU architectures: **x86_64**, **ARM64 (AArch64)**, and **RISC-V (RV64I)**.

---

## 1. Core Instruction Classification Matrix

Assembly languages map machine code instructions into human-readable mnemonics. The table below compares how standard programming operations are expressed across all three architectures.

| Operation Category | Functional Description | x86_64 Mnemonic (Intel) | ARM64 Mnemonic (AArch64) | RISC-V Mnemonic (RV64) |
|---|---|---|---|---|
| **Data Movement** | Copy data between registers or memory | `mov dest, src` | `mov dest, src` | `mv dest, src` (pseudo) |
| **Memory Load** | Read data from memory address into register | `mov reg, [addr]` | `ldr reg, [addr]` | `ld reg, offset(base)` |
| **Memory Store** | Write register value out to memory address | `mov [addr], reg` | `str reg, [addr]` | `sd reg, offset(base)` |
| **Addition** | Add two operands | `add dest, src` | `add dest, src1, src2` | `add dest, src1, src2` |
| **Subtraction** | Subtract second operand from first | `sub dest, src` | `sub dest, src1, src2` | `sub dest, src1, src2` |
| **Multiplication** | Multiply operands | `imul dest, src` | `mul dest, src1, src2` | `mul dest, src1, src2` |
| **Division** | Divide operands | `idiv src` | `sdiv dest, src1, src2` | `div dest, src1, src2` |
| **Logical AND** | Bitwise AND | `and dest, src` | `and dest, src1, src2` | `and dest, src1, src2` |
| **Logical OR** | Bitwise OR | `or dest, src` | `orr dest, src1, src2` | `or dest, src1, src2` |
| **Logical XOR** | Bitwise XOR / Clear register | `xor dest, src` | `eor dest, src1, src2` | `xor dest, src1, src2` |
| **Shift Left** | Logical Shift Left (Multiply by $2^n$) | `shl dest, count` | `lsl dest, src, shift` | `sll dest, src1, src2` |
| **Shift Right** | Logical Shift Right (Divide by $2^n$) | `shr dest, count` | `lsr dest, src, shift` | `srl dest, src1, src2` |
| **Compare** | Compare two values and update flags | `cmp op1, op2` | `cmp op1, op2` | *Uses explicit branch checks* |
| **Unconditional Jump**| Branch unconditionally to target label | `jmp label` | `b label` | `j label` (pseudo) / `jal zero, label` |
| **Subroutine Call** | Call function (saves return address) | `call label` | `bl label` | `jal ra, label` |
| **Subroutine Return**| Return from function | `ret` | `ret` | `ret` (pseudo) / `jalr zero, 0(ra)` |

---

## 2. Conditional Branching & Comparison Guide

Conditional branching allows assembly programs to execute decisions (`if`/`else`, loops).

### 2.1 x86_64 Conditional Jumps
x86_64 uses a dedicated `FLAGS` register updated by arithmetic operations and explicit `cmp op1, op2` instructions (which computes `op1 - op2` internally without saving the result).

| x86_64 Mnemonic | Condition Name | Flag State Checked | High-Level Equivalent |
|---|---|---|---|
| `je` / `jz` | Jump if Equal / Jump if Zero | `ZF = 1` | `if (a == b)` |
| `jne` / `jnz` | Jump if Not Equal / Not Zero | `ZF = 0` | `if (a != b)` |
| `jg` / `jnle` | Jump if Greater (Signed) | `ZF = 0` and `SF = OF` | `if (a > b)` |
| `jge` / `jnl` | Jump if Greater or Equal (Signed) | `SF = OF` | `if (a >= b)` |
| `jl` / `jnge` | Jump if Less (Signed) | `SF != OF` | `if (a < b)` |
| `jle` / `jng` | Jump if Less or Equal (Signed) | `ZF = 1` or `SF != OF` | `if (a <= b)` |
| `ja` / `jnbe` | Jump if Above (Unsigned) | `CF = 0` and `ZF = 0` | `if (a > b)` (unsigned) |
| `jb` / `jnae` | Jump if Below (Unsigned) | `CF = 1` | `if (a < b)` (unsigned) |

### 2.2 ARM64 (AArch64) Conditional Branches
ARM64 updates its `NZCV` (Negative, Zero, Carry, oVerflow) condition flags when executing instructions with an `s` suffix (e.g., `adds`, `subs`) or explicit `cmp op1, op2`. Branches use `b.condition label`.

| ARM64 Mnemonic | Condition Name | Flag State Checked | High-Level Equivalent |
|---|---|---|---|
| `b.eq` | Branch if Equal | `Z = 1` | `if (a == b)` |
| `b.ne` | Branch if Not Equal | `Z = 0` | `if (a != b)` |
| `b.gt` | Branch if Greater Than (Signed) | `Z = 0` and `N = V` | `if (a > b)` |
| `b.ge` | Branch if Greater or Equal (Signed) | `N = V` | `if (a >= b)` |
| `b.lt` | Branch if Less Than (Signed) | `N != V` | `if (a < b)` |
| `b.le` | Branch if Less or Equal (Signed) | `Z = 1` or `N != V` | `if (a <= b)` |
| `cbz reg, label` | Compare and Branch if Zero | Checks if `reg == 0` | `if (reg == 0)` |
| `cbnz reg, label`| Compare and Branch if Not Zero | Checks if `reg != 0` | `if (reg != 0)` |

### 2.3 RISC-V (RV64I) Fused Compare-and-Branch Instructions
RISC-V deliberately omits dedicated condition flag registers to simplify hardware pipelining. Instead, it combines comparison and branching into single atomic instructions.

| RISC-V Mnemonic | Condition Name | Functional Operation | High-Level Equivalent |
|---|---|---|---|
| `beq src1, src2, label` | Branch if Equal | If `src1 == src2`, branch | `if (a == b)` |
| `bne src1, src2, label` | Branch if Not Equal | If `src1 != src2`, branch | `if (a != b)` |
| `blt src1, src2, label` | Branch if Less Than (Signed) | If `src1 < src2`, branch | `if (a < b)` |
| `bge src1, src2, label` | Branch if Greater or Equal (Signed)| If `src1 >= src2`, branch | `if (a >= b)` |
| `bltu src1, src2, label`| Branch if Less Than (Unsigned) | If `src1 < src2` (unsigned), branch | `if (a < b)` (unsigned) |
| `bgeu src1, src2, label`| Branch if Greater or Equal (Unsigned)| If `src1 >= src2` (unsigned), branch | `if (a >= b)` (unsigned) |

---

## 3. Practical Syntax Comparison: Control Flow Loop

To understand how these syntaxes function in real code, below is an identical loop (`for (int i = 0; i < 10; i++) sum += i;`) implemented across all three architectures.

### 3.1 x86_64 Implementation (Intel Syntax)
```assembly
    mov ecx, 0          ; ecx = i = 0
    mov eax, 0          ; eax = sum = 0

loop_start:
    cmp ecx, 10         ; Compare i with 10
    jge loop_end        ; If i >= 10, jump out of loop

    add eax, ecx        ; sum += i
    inc ecx             ; i++
    jmp loop_start      ; Repeat loop

loop_end:
    ; Final sum is in eax
```

### 3.2 ARM64 Implementation (AArch64 Syntax)
```assembly
    mov w0, #0          ; w0 = i = 0
    mov w1, #0          ; w1 = sum = 0

loop_start:
    cmp w0, #10         ; Compare i with 10
    b.ge loop_end       ; If i >= 10, branch out of loop

    add w1, w1, w0      ; sum += i
    add w0, w0, #1      ; i++
    b loop_start        ; Repeat loop

loop_end:
    ; Final sum is in w1
```

### 3.3 RISC-V Implementation (RV64I Syntax)
```assembly
    li t0, 0            ; t0 = i = 0 (li = load immediate)
    li t1, 0            ; t1 = sum = 0
    li t2, 10           ; t2 = limit = 10

loop_start:
    bge t0, t2, loop_end ; If i >= limit, branch out of loop

    add t1, t1, t0      ; sum += i
    addi t0, t0, 1      ; i++ (addi = add immediate)
    j loop_start        ; Repeat loop

loop_end:
    ; Final sum is in t1
```
