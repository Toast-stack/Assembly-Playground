# 🧵 Assembly Breakdown: Hello World

## Overview
This project walks through a complete transformation of a simple C++ program into its compiled x64 assembly output on Windows. It's designed for beginners who want to understand how lines like `std::cout << "Hello World!"` end up as instructions like `mov`, `lea`, and `call`.

By comparing the original source code to the generated assembly line by line, this repo helps demystify how compilers translate human logic into machine operations.

## 💡 Source Code

```cpp
#include <iostream>

int main() {
    std::cout << "Hello World!\n";
}
```
A minimal C++ program using std::court.

## 🔍 What This Project Explains
- How the compiler sets up a stack frame using `push rbp`, `mov rbp, rsp`, and `sub rsp, 32`
- Why Windows x64 calling conventions use `rcx`, `rdx`, and `r8` to pass arguments
- How static strings like `"Hello World!\n"` are stored using `.ascii` and accessed via `rip`-relative addressing
- What functions like `__main` and `_ZStls...` represent during iostream calls
- How the function exits cleanly using `mov eax, 0`, `add rsp, 32`, and `ret`

## 🧠 Assembly Concepts Covered
| Assembly Instruction | Role | Equivalent C++ Concept |
| --- | --- | ---|
|`push rbp` | Save previous base pointer | Begin `main()` function |
| `sub rsp, 32` | Allocate stack space | Set up workspace |
| `lea rdx, .LC0[rip]` | Load pointer to string | `"Hello World!\n"`|
| `call __main` | Runtime preparation | (internal setup) |
| `mov rcx,rax` | Load `std::cout` into first arg slot | `std::cout` stream |
| `call operator<<` | Call iostream printer | `std::court << "..."` |
| `mov eax, 0` | Set return value | `return 0;` |

## 📦 Files in This Repo
- `Hello.cpp` - Original C++ source code
- `Hello.asm` - Generated assembly from GCC using `-S -masm=intel`
- `README.md` - Line-by-line annotated breakdown

## 🎯 Goal
Make assembly transparent, approachable, and rewarding to learn, one instruction at a time.
