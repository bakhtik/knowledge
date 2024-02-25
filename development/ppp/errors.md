# Errors

> "I realized that from now on a large part of my life would be spent finding and correcting my own mistakes." - Maurice Wilkes, 1949

- [Introduction](#introduction)
- [Sources of errors](#sources-of-errors)
- [Compile-time errors](#compile-time-errors)
- [Link-time errors](#link-time-errors)

## Introduction

Errors classification:

- *Compile-time errors:* Errors found by compiler.
  - Syntax errors
  - Type errors
- *Link-time errors:* Errors found by linker during combining object files.
- *Run-time errors:* Errors found by checks in a running program.
  - Errors detected by the computer (hardware/OS)
  - Errors detected by a library
  - Errors detected by a user code
- *Logic errors:* Errors found by the programmer due to erroneous results.

When we write programs, errors are natural and unavoidable. Avoiding, finding, and correcting errors take 90% of the effort when developing serious software.

Approach to produce acceptable software:

- Organize software to minimize errors.
- Eliminate most of the errors through debugging and testing.
- Make sure that the remaining errors are not serious.

## Sources of errors

- *Poor specification:* We cannot adequately examine the "dark corners" in this case.
- *Incomplete programs:* Our aim is to know when we have handled all cases.
- *Unexpected arguments:* If a function is given bad argument, we have a problem.
- *Unexpected input:* A program makes many assumptions about inputs (from keyboard, file, GUI, network, etc.).
- *Unexpected state:* Most programs keep a lot of data ("state") around for use by different part of the system. What if such data is incomplete or wrong?
- *Logical errors:* The code is simply doesn't do what it was supposed to do.

We can use this list  as a checklist when we are considering how far we have come with a program.

## Compile-time errors

You compiler is your first line of defense against errors. Before generating code the compiler analyzes code to detect syntax errors and type errors.

Let's consider this simple function:

```c++
int area(int length, int width); // calculate are of a rectange
```

### Syntax errors

```c++
int s1 = area(7;    // error: ) missing
int s2 = area(7)    // error: ; missing
Int s3 = area(7);    // error: Int is not a type
int s4 = area('7);    // error: non-terminated character (' missing)
```

These are syntax errors - they are not well formed according to the C++ grammar.

The error reports are often cryptic and can refer to a line further because the compiler may have to read a bit further than the error to be sure that there really is an error.

### Type errors

The type errors show mismatches between the types you declared (or forgot to declare) for your variables, functions, etc. and the types of values of expressions you assign to them, pass as function arguments, etc.

```c++
int x0 = arena(7);  // error: undeclared function
int x1 = area(7);   // error: wrong number of arguments
int x2 = area("seven", 2);   // error: 1st argument has a wrong type
```

In C++, every function call must provide the expected number of arguments, of the right type, and in the right order. When the type system is used appropriately, this can be a powerful tool for avoiding run-time errors.

## Link-time errors

A program consists of several separately compiled parts, called *translation units*. Every function in a program must by declared with exactly the same type (both the return type and the argument types) in every translation unit in which it is used. We use header files to ensure that. Every function must also be defined exactly once in a program. If either of these rules is violated, the linker will give an error.

Definitions of the functions with the same name but different types will not match and will be ignored.

Note that a misspelled function name doesn't usually give a linker error. Instead, its the compiler who gives an error to an undeclared function.

The linkage rules stated above also hold for all other entities like variables and types:

- exactly one definition
- many declarations that agree exactly on definition's type
