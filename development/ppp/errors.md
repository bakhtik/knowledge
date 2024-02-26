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

## Run-time errors

Bad function arguments can lead to run-time errors. There are two alternatives to deal with this:

- Let the caller of the function deal with bad arguments.
- Let the called function deal with bad arguments.

### The caller deals with errors

This alternative is "Let the user beware!" approach. For example if we are using a library function that cannot modify.

This approach leads to the messy, error-prone and "brittle" code that breaks easily. And the approach imply called function implementation details exposure.

### The callee deals with errors

A "function must check its own arguments" approach ("the callee checks"). 

One benefit of the latter approach is that the argument-checking code is in one place where the arguments are to be used.

Reasons why don't people do that approach always:

- *We can't modify the function definition:* a library function, in example.
- *The called function doesn't know what to do in case of error:* Also a typical case for library function.
- *The called function doesn't know where it was called from:* Sometimes you want an error message to be more specific.
- *Performance:* For some programs, introducing checking overhead can be critical.

Check your arguments in a function unless you have a good reason no to.

### Error reporting

What should you do when you found an error?

Sometimes you can return an "error value".

```c++
// calculate area of a rectangle
// return -1 to indicate a bad argument
int area(int length, int width)
{
    if (length<=0 || width<=0) return -1;
    return length*width;
}
```

Called function do the checking, while caller can handle the error as desired.

Problems with the approach:

- Both the called function and all callers must test.
- A caller can forget to test.
- Many function do not have an "extra" return value that can use to indicate an error.

## Exceptions

The fundamental idea is to separate detection of an error (which should be done in a called function) from the handling of an error (which should be done in the calling function) while ensuring that a detected error cannot be ignored. Nothing makes errors handling easy, but exceptions make it easier.

The basic idea is that if a function finds an error that it cannot handle, it does not `return` normally; instead, it `throw`s and exception indicating what went wrong. Any direct or indirect caller can `catch` the exception, that is, specify what to do if the called code used `throw`. A function expresses interest in exceptions by using a `try`-block listing the kinds of exceptions it wants to handle in the `catch` parts of the `try`-block. If no caller catches an exception, the program terminates.

### Bad arguments

```c++
class Bad_area {};  // a type specifically for reporting errors from area()

// calculate area of a rectangle;
// trow a Bad_area exception in case of a bad argument
int area(int length, int width)
{
    if (length<=0 || width<=0) throw Bad_area{};
    return length*width;
}

int main()
{
    try {
        int x = -1;
        int y = 2;

        int area1 = area(x,y);
    }
    catch (Bad_area) {
        cout << "Oops! bad arguments to area()\n";
    }
}
```

`Bad_area` is a new type with the only purpose to provide something unique to `throw` from `area()` so that some `catch` can recognize it as the kind of exception thrown by `area()`.

The notation `throw Bad_are{}` means "Make an object of type `Bad_area` and `throw` it.

Note how the handling of the error is cleanly separated from the detection of the error: `main()` knows nothing about who `throw`ed the exception, and called function knows nothing about which function  (if any) cares to `catch` the exception.

### Range errors

In the context of C++, we often refer to "collections of data" as *containers*. The most common and useful standard library container is the `vector`.

What happens if we try to use an element of the `vector` with an index (subscript) that isn't in the valid range [0:v.size())? The general notation [low:high) means indices from low to high-1, that is, including low but not high.

In this case we will get an *off-by-one error*, a *range error* because the index wasn't in the range required by the `vector`, and a *bounds error* because the index was not within the limits of the `vector`.

Range-`for` loops cannot get out of bounds, but they also don't give indices information without extra effort.

The subscript operation (called `vector::operator[]`) of `vector` knows the size of the `vector`, so it can check. If that check fails, the subscript operation throws an exception of type `out_of_range`.

```c++
int main()
{
    try {
        vector<int> v;
        for (int x; cin>>x; )
            v.push_back(x);
        for (int i=0; i<=v.size(); ++i)
            cout << "v[" << i << "] == " << v[i] << '\n';
    } catch (out_of_range) {
        cerr << "Oops! Range error\n";
        return 1;
    } catch (...) {     // catch all other exceptions
        cerr << "Exception: something went wrong\n";
        return 2;
    }
}
```

