Here is the comprehensive, compact master reference for C. It covers the full lifecycle, from preprocessor directives to memory layout, using dense, highly targeted code blocks.
### 1. Preprocessor, Headers & Scope
Headers are contracts. Macros do text replacement before compilation. Code blocks {} create isolated local scopes anywhere.
```c
#include <stdio.h>  // Standard I/O prototypes
#include <stdlib.h> // Memory management prototypes

#define MAX_BUFFER 256 // Macro: Replaced textually by compiler

void scope_demo() {
    int a = 10;
    {   // Arbitrary scope block
        int a = 20; // Shadows outer 'a'
        int temp = 5; 
    }   // 'temp' and inner 'a' are destroyed here
}

```
### 2. Types, Enums & Unions
C has primitives, grouped types (enum), and shared-memory types (union).
```c
typedef unsigned char byte; // Custom type alias

typedef enum { IDLE, RUNNING, ERROR } State; // 0, 1, 2

typedef union {
    int as_int;
    char as_bytes[4];
} Data; // Shares the EXACT same memory address. Size = 4 bytes total.

```
### 3. C's "Classes": Structs
Structs group data. To simulate object-oriented behavior, pass a pointer to the struct into your functions.
```c
typedef struct {
    int id;
    const char* name;
} User;

// "Method" equivalent
void init_user(User* u, int id, const char* name) {
    u->id = id;
    u->name = name; // Pointers use -> instead of .
}

```
### 4. Pointer & Function Variants
Everything is an address. Functions can return and accept addresses, or be addresses themselves.
```c
// 1. Standard Value
int add(int a) { return a + 1; }

// 2. Pointer Return (Must point to heap or static, NEVER local stack variable)
int* get_static() { static int x = 5; return &x; }

// 3. Void Pointer (Generic, can cast to anything)
void* process_raw(void* data) { return data; }

// 4. Function Pointer (Passing a function as a variable)
void execute(void (*func_ptr)(int), int val) { func_ptr(val); }

```
### 5. String Mastery & Function Input
Strings are just char arrays ending in \0. How you pass them to functions matters immensely for safety.
```c
// STRING INPUT 1: Read-Only (Use 'const' for safety)
// Accepts both Literals ("Text") and Arrays (char buf[])
void read_string(const char* str) {
    if (str) printf("Read: %s\n", str);
}

// STRING INPUT 2: Writable 
// MUST be passed a stack array or heap buffer. Literals will CRASH.
void mutate_string(char* str) {
    if (str && str[0] != '\0') str[0] = 'X'; 
}

void string_demo() {
    char *literal = "Hello";    // Read-only memory.
    char buffer[] = "Hello";    // Writable stack memory.
    
    read_string(literal);       // Safe
    mutate_string(buffer);      // Safe -> "Xello"
    // mutate_string(literal);  // FATAL CRASH (Segmentation Fault)
}

```
### 6. Safe String Operations
Always use bounded functions (n or sn) to prevent buffer overflows.
```c
#include <string.h>

void safe_ops() {
    char dest[20];
    const char* src = "Critical Data";
    
    // SAFE COPY: snprintf is modern and guarantees null-termination
    snprintf(dest, sizeof(dest), "%s", src);
    
    // SAFE CONCATENATION
    strncat(dest, " Extra", sizeof(dest) - strlen(dest) - 1);
    
    // SAFE COMPARE
    if (strncmp(dest, src, 5) == 0) { /* First 5 chars match */ }
}

```
### 7. Memory Management (Heap vs. Stack)
If you don't manage the heap, the OS will run out of memory.
```c
void memory_lifecycle() {
    // 1. ALLOCATE: Raw uninitialized bytes
    int* arr1 = malloc(5 * sizeof(int)); 
    
    // 2. CALLOC: Allocated AND zeroed out
    int* arr2 = calloc(5, sizeof(int));
    
    if (!arr1 || !arr2) return; // Always check for NULL (Out of memory)

    // 3. REALLOC: Resize existing block (moves data if necessary)
    int* temp = realloc(arr1, 10 * sizeof(int));
    if (temp) arr1 = temp; // Only reassign if successful to avoid losing original ptr

    // 4. FREE: Release memory back to OS
    free(arr1); arr1 = NULL; // Prevent dangling pointers
    free(arr2); arr2 = NULL; 
}

```
### 8. File I/O
Interacting with the disk using file pointers.
```c
void write_and_read() {
    // WRITE
    FILE* fw = fopen("data.txt", "w"); // "w" = write, "a" = append, "wb" = write binary
    if (fw) {
        fprintf(fw, "Line %d\n", 1);
        fclose(fw);
    }

    // READ
    char buffer[256];
    FILE* fr = fopen("data.txt", "r");
    if (fr) {
        while (fgets(buffer, sizeof(buffer), fr)) {
            printf("Read: %s", buffer);
        }
        fclose(fr);
    }
}

```
