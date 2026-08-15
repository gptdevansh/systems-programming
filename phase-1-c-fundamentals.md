# Phase 1: C Fundamentals

This file is the core study map for the first phase of the systems programming roadmap. The goal is to build a strong mental model of hardware, memory, and C semantics before moving into Rust.

---

## How to Study This Phase

Treat this phase as a conceptual foundation, not just a reading list.

### Success criteria

By the end of this phase, you should be able to:

- explain how a program is represented in memory
- reason about stack vs heap lifetime and ownership
- explain what pointers actually hold
- identify common C bugs and why they happen
- understand how compilation and linking work
- describe how the OS and hardware interact with a running process

### Study loop for each topic

1. Read the concept
2. Write a small C example
3. Run it and observe the behavior
4. Debug it using compiler warnings, GDB, or sanitizers
5. Re-explain the concept in plain language

### Practical exercises

- Create a program that prints memory addresses of variables
- Write a simple struct and show how padding/alignment works
- Build a pointer demo that exposes dangling references
- Create a small program with a buffer overflow and inspect it with ASan
- Compare stack allocation vs heap allocation in a few small examples

---

## 0. Mental Model — Before C

### 0.1 What Is a Program?

- Source code
- Executable
- Instructions
- Data
- State
- Input
- Output

### 0.2 What Is a Computer?

- CPU
- Memory
- Storage
- I/O
- Bus
- Devices

### 0.3 Hardware vs Software

- Hardware
- Firmware
- Operating system
- Application
- Runtime

### 0.4 Abstraction Layers

- Hardware
- Machine code
- Assembly
- C
- Libraries
- Operating system
- Application

### 0.5 What Actually Happens When Code Runs?

- Load
- Decode
- Execute
- Memory access
- Register operations
- Branching
- Function calls

---

## 1. C Language Fundamentals

### 1.1 C's Philosophy

- Low-level control
- Minimal runtime
- Manual resource management
- Compilation model
- Undefined behavior
- Portability

### 1.2 Program Structure

- `main`
- Statements
- Expressions
- Blocks
- Scope
- Translation units

### 1.3 Types

- `char`
- `short`
- `int`
- `long`
- `long long`
- `float`
- `double`
- `_Bool`
- `void`

### 1.4 Type Properties

- Size
- Alignment
- Representation
- Signedness
- Range
- Precision

### 1.5 Constants

- Integer literals
- Floating literals
- Character constants
- String literals
- Hexadecimal
- Octal
- Binary representation

### 1.6 Variables

- Declaration
- Definition
- Initialization
- Assignment
- Lifetime
- Scope
- Storage duration

### 1.7 Operators

- Arithmetic
- Relational
- Logical
- Bitwise
- Assignment
- Increment/decrement
- Conditional
- `sizeof`
- Cast

### 1.8 Control Flow

- `if`
- `else`
- `switch`
- `for`
- `while`
- `do while`
- `break`
- `continue`
- `goto`

---

## 2. Memory — ⭐⭐⭐⭐⭐

This is one of the most important branches in the entire roadmap.

### 2.1 Memory Fundamentals

- Bits
- Bytes
- Addresses
- Address space
- Memory cells

### 2.2 Memory Representation

- Binary
- Decimal
- Hexadecimal
- Two's complement
- Integer representation
- Floating-point representation
- IEEE 754

### 2.3 Memory Layout

- Code/Text segment
- Read-only data
- Initialized data
- BSS
- Heap
- Stack

### 2.4 Stack

- Stack frame
- Stack pointer
- Frame pointer
- Local variables
- Return address
- Function arguments
- Stack growth
- Stack overflow

### 2.5 Heap

- Dynamic allocation
- Allocation metadata
- Fragmentation
- Allocation lifetime
- Deallocation

### 2.6 C Allocation

- `malloc`
- `calloc`
- `realloc`
- `free`

### 2.7 Memory Ownership

- Who allocated?
- Who owns?
- Who accesses?
- Who modifies?
- Who releases?

### 2.8 Memory Errors

- Memory leak
- Double free
- Use-after-free
- Dangling pointer
- Buffer overflow
- Out-of-bounds access
- Uninitialized memory
- Invalid free
- Heap corruption
- Stack corruption

### 2.9 Memory Debugging

- Valgrind
- AddressSanitizer
- UndefinedBehaviorSanitizer
- GDB

---

## 3. Pointers — ⭐⭐⭐⭐⭐

Do not rush this chapter.

### 3.1 Pointer Fundamentals

- Address
- Pointer variable
- Dereferencing
- Address-of operator
- Pointer types

### 3.2 Pointer Arithmetic

- Increment
- Decrement
- Addition
- Subtraction
- Pointer difference

### 3.3 Pointer Relationships

- Pointer → value
- Pointer → pointer
- Pointer → array
- Pointer → struct
- Pointer → function

### 3.4 Pointer Types

- `void *`
- `char *`
- `const T *`
- `T *const`
- `const T *const`

### 3.5 Pointer Safety

- Null pointer
- Dangling pointer
- Wild pointer
- Invalid pointer
- Lifetime

### 3.6 Function Pointers

- Function address
- Callback
- Dispatch table
- Function pointer arrays

### 3.7 Advanced Pointers

- Pointer-to-pointer
- Pointer to array
- Array of pointers
- Function returning pointer
- Pointer to function returning pointer

---

## 4. Arrays & Strings

### 4.1 Arrays

- Contiguous memory
- Indexing
- Array size
- Array lifetime
- Multidimensional arrays

### 4.2 Array ↔ Pointer Relationship

- Array decay
- Pointer arithmetic
- Passing arrays to functions

### 4.3 Strings

- Null terminator
- String literals
- Character arrays
- String length
- String copying
- String comparison

### 4.4 C String Problems

- Buffer overflow
- Missing terminator
- String lifetime
- Immutable string literals
- Unsafe copying

---

## 5. Functions & Calling Mechanism

### 5.1 Functions

- Declaration
- Definition
- Prototype
- Parameters
- Return value

### 5.2 Function Call Mechanics

- Call stack
- Stack frame
- Arguments
- Return address
- Return value

### 5.3 Parameter Passing

- Pass-by-value
- Passing pointers
- Simulating pass-by-reference

### 5.4 Recursion

- Recursive call
- Stack growth
- Base case
- Stack overflow

### 5.5 Calling Conventions

- Registers
- Stack arguments
- Return registers
- ABI

---

## 6. Structs, Unions & Enums

### 6.1 Structures

- Fields
- Memory layout
- Padding
- Alignment
- Nested structs

### 6.2 Struct Pointers

- `->`
- Pointer-to-struct
- Dynamic structs

### 6.3 Structure Passing

- Pass by value
- Pass by pointer

### 6.4 Unions

- Shared storage
- Type punning
- Representation

### 6.5 Enums

- Enumeration constants
- Representation
- State modeling

### 6.6 Bitfields

- Bit-level storage
- Packing
- Hardware-oriented structures

---

## 7. Type System — ⭐⭐⭐⭐

### 7.1 Type Conversion

- Implicit conversion
- Explicit conversion
- Integer promotion
- Usual arithmetic conversions

### 7.2 Qualifiers

- `const`
- `volatile`
- `restrict`

### 7.3 Type Aliases

- `typedef`

### 7.4 Composite Types

- Arrays
- Pointers
- Functions
- Structs
- Unions

### 7.5 Type Compatibility

### 7.6 Strict Aliasing

### 7.7 Effective Type

---

## 8. Compilation — ⭐⭐⭐⭐⭐

Do not treat `gcc file.c` as magic. Understand what actually happens.

### 8.1 Source → Executable

```text
C Source
  ↓
Preprocessor
  ↓
Compiler
  ↓
Assembly
  ↓
Assembler
  ↓
Object File
  ↓
Linker
  ↓
Executable
```

### 8.2 Preprocessor

- `#include`
- `#define`
- Macros
- Conditional compilation
- Header guards

### 8.3 Compiler

- Lexing
- Parsing
- Semantic analysis
- Optimization
- Code generation

### 8.4 Assembly

- Registers
- Instructions
- Labels
- Stack operations
- Calling conventions

### 8.5 Assembler

- Assembly → object code

### 8.6 Object Files

- Sections
- Symbols
- Relocations

### 8.7 Linker

- Symbol resolution
- Relocation
- Static linking
- Dynamic linking

### 8.8 Executable Formats

- ELF
- PE
- Mach-O

---

## 9. Assembly & Machine-Level Understanding

You do not need to become an assembly expert, but you must understand the machine model.

### 9.1 CPU

- Registers
- ALU
- Control unit
- Instruction pointer

### 9.2 Instructions

- Load
- Store
- Move
- Add
- Subtract
- Compare
- Jump
- Call
- Return

### 9.3 Registers

- General purpose
- Stack pointer
- Instruction pointer
- Flags

### 9.4 Machine Code

- Opcodes
- Operands
- Instruction encoding

### 9.5 Assembly ↔ C

- Variable → register/memory
- Function → call
- Loop → branch
- Pointer → address calculation

---

## 10. Undefined Behavior — ⭐⭐⭐⭐⭐

This deserves its own major branch.

### 10.1 What Is Undefined Behavior?

### 10.2 Why C Has UB

### 10.3 Examples

- Out-of-bounds access
- Use-after-free
- Signed overflow
- Invalid shift
- Invalid pointer dereference
- Uninitialized reads
- Data races

### 10.4 Compiler Assumptions

### 10.5 Optimization vs UB

### 10.6 Why "It Worked on My Machine" Is Not Proof

---

## 11. Storage Duration & Lifetime

- Automatic
- Static
- Thread-local
- Allocated
- Object lifetime
- Scope vs lifetime
- Ownership vs lifetime

> This branch will later make Rust ownership and lifetimes much easier.

---

## 12. Linkage & Visibility

- Local scope
- Global scope
- Internal linkage
- External linkage
- `static`
- `extern`
- Symbols
- Symbol visibility

---

## 13. C Modules & Build System

- Header files
- Source files
- Translation units
- Include guards
- Separate compilation
- Static libraries
- Shared libraries
- ABI
- API vs ABI
- Make
- CMake

> This becomes useful later when understanding Rust crates, modules, and Cargo.

---

## 14. File I/O & Operating-System Interface

- Files
- File descriptors
- `open`
- `read`
- `write`
- `close`
- Standard streams: `stdin`, `stdout`, `stderr`
- Buffering
- System calls
- C library vs kernel

> This distinction is extremely important.

---

## 15. Processes — ⭐⭐⭐⭐⭐

### 15.1 Program vs Process

### 15.2 Process Memory

- Code
- Data
- Heap
- Stack

### 15.3 Process Creation

- `fork`
- `exec`

### 15.4 Process Termination

### 15.5 Exit Status

### 15.6 Parent/Child Processes

### 15.7 Process IDs

### 15.8 Environment Variables

### 15.9 Pipes

### 15.10 Signals

---

## 16. Threads & Concurrency — ⭐⭐⭐⭐⭐

- Process vs thread
- Thread stack
- Shared memory
- Race conditions
- Data races
- Mutex
- Semaphore
- Condition variables
- Atomic operations
- Memory ordering
- Deadlocks
- Starvation
- Lock-free programming

> This branch is extremely valuable before Rust concurrency.

---

## 17. Virtual Memory — ⭐⭐⭐⭐⭐

- Physical memory
- Virtual memory
- Virtual addresses
- Physical addresses
- Page
- Page table
- MMU
- TLB
- Page fault
- Memory mapping
- `mmap`
- Copy-on-write

> This will completely change how you think about pointers.

---

## 18. System Calls

- User mode
- Kernel mode
- Privilege levels
- System call interface
- System call boundary
- Arguments
- Return values
- `errno`
- C library vs system call

---

## 19. Networking — ⭐⭐⭐⭐⭐

### 19.1 Network Fundamentals

- IP
- MAC
- Port
- Packet
- Frame

### 19.2 TCP/IP

- TCP
- UDP
- IP
- DNS
- HTTP

### 19.3 Sockets

- Socket
- Bind
- Listen
- Accept
- Connect
- Send
- Receive

### 19.4 Server Architecture

- Single-threaded
- Multi-process
- Multi-threaded
- Event-driven

### 19.5 Network Concurrency

---

## 20. Data Structures in C

Not just for DSA. Use them to understand memory, layout, and pointers.

- Array
- Dynamic array
- Linked list
- Doubly linked list
- Stack
- Queue
- Hash table
- Tree
- Binary search tree
- Heap
- Graph

> For every structure ask: where exactly is every byte stored?

---

## 21. Memory Allocator

This is an elite-level foundation topic.

- Why allocators exist
- Allocation strategies
- Free lists
- Block metadata
- Splitting
- Coalescing
- Fragmentation
- Alignment
- `malloc` internals
- Build your own allocator

> If you understand this deeply, you will understand a huge amount of systems programming.

---

## 22. Debugging & Observability

- GDB
- Breakpoints
- Watchpoints
- Stack frames
- Registers
- Memory inspection
- Core dumps
- Valgrind
- Sanitizers
- `strace`
- `ltrace`
- `objdump`
- `readelf`
- `nm`
- `perf`

---

## 23. Security Fundamentals

- Memory safety
- Buffer overflow
- Stack smashing
- Heap exploitation
- Use-after-free
- Integer overflow
- Format string vulnerability
- Command injection
- ASLR
- DEP/NX
- Stack canaries
- Control-flow integrity

---

## 24. C Standard Library Internals

- `stdio`
- `stdlib`
- `string`
- `stdint`
- `stdbool`
- `stddef`
- `errno`
- `time`
- `math`

> Understand the difference between library behavior and OS/kernel behavior.

---

## 25. Hardware Interaction

- Memory-mapped I/O
- Registers
- Interrupts
- DMA
- Device drivers
- Volatile memory
- Embedded C
- Microcontrollers

---

## 26. Advanced C Concepts

- Function-like macros
- Variadic functions
- `va_list`
- `setjmp`
- `longjmp`
- Flexible array members
- Compound literals
- Designated initializers
- `_Generic`
- `_Atomic`
- `_Alignof`
- `_Alignas`

> These are not all essential for the first Rust transition, but they are highly useful for deep C mastery.

---

## Final Takeaway

The practical objective of this phase is not just to memorize C syntax, but to understand:

- how memory is laid out
- how pointers relate to addresses
- how the compiler transforms code
- why undefined behavior is dangerous
- how the OS and hardware interact with user programs

Once these ideas are clear, the move into Rust ownership, borrowing, lifetimes, and concurrency becomes significantly easier.
