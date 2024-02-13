# Computation

> "If it doesn't have to produce correct results, I can make it arbitrarily fast." - Gerald M. Weinberg

From a broad view, all that a program ever does is to compute; that is, it takes some inputs and produces some output.

To deal with input, a program usually contains some data, referred to as its *data structures* or its *state*.

From a programming point of view the most important categories of input and output are "to/from another program" and "to/from other parts of a program". 

The key questions in programming are:

- How do we express a program as a set of cooperating parts?
- How can they share and exchange data?

![computation](img/computation.png)

The abbreviation I/O stands for "input/output". In this case, the output from one part of the code is the input for the next part. What such "part of a program" share is data stored in main memory, on persistent storage devices, or transmitted over network connections. By "parts of a program" we mean entities such as a function.

Inputs to a functions are called *arguments* and outputs from them are called *results*.

By *computation* we mean the act of producing some outputs based on some inputs.

## Objectives and tools

Our job as programmers is to express computations:

1. Correctly
2. Simply
3. Efficiently

In this order only. Concerns about correctness, simplicity, and efficiency become ours the minute we start writing code for others and accept responsibility to do that well. 

Our main tool for organizing a program and our thoughts as we program is to break up a big computation into many little ones:

- *Abstraction*: Hide details that we don't need to use a facility ("implementation details") behind a convenient and general interface.
- *"Divide and conquer"*: Here we take a large problem and divide it into several little ones. Each of the resulting problems is significantly smaller than the original.

We are not very good at dealing with large problems. We simply cannot write and maintain large monolithic programs, so we are composing large programs with a set of small parts.

A good library, supplying useful facilities for expression ideas, can crucially affect the way we distribute functionality into different part of a program. If you use existing library you can safe yourself a lot of work on programming, on testing, and documentation. This is a first example of partitioning a program using abstractions.

Good programmers and system designers know that concerns about code *structure* and *organization* lie at the heart of good software and that ignoring structure leads to expensive messes.
