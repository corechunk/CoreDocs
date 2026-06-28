# 🏛️ Struct Alignment and Memory Padding Rules

## 1. Physical Memory Alignment Alignment
Modern CPUs (x86_64, ARM, RISC-V) access memory most efficiently when data addresses are aligned to multiples of their natural size (e.g., a 4-byte integer aligned to an address divisible by 4).

## 2. Compiler Padding Insertion
To satisfy hardware alignment constraints, language compilers automatically insert empty "padding bytes" between struct fields.

```c
struct SystemHeader {
    uint8_t  flag;      // 1 byte
    // 3 bytes of padding silently inserted here by compiler
    uint32_t address;   // 4 bytes (aligned to 4-byte boundary)
    uint8_t  status;    // 1 byte
    // 3 bytes of trailing padding inserted here to round total size to 8
};
```

- **Total Data Bytes:** 6 bytes
- **Actual Memory Occupied:** 12 bytes (`sizeof(struct SystemHeader)`)

## 3. Distributed Network Serialization Warning
When streaming raw structs over network sockets or sharing across cross-compiled ABI boundaries (e.g., C desktop host to ARM Android client), hardcoded binary memory layout assumptions fail due to compiler padding variations.
- **Solution:** Use explicit packed attributes (`__attribute__((packed))`) for raw binary formats, or serialize objects into universal plain-text formats like **JSON** to guarantee platform independence.
