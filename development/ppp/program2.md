# Completing a Program

> "It ain't over till the fat lady sings." - Opera proverb

Writing a program involves gradually refining your ideas of what you want to do and how you want to express it.

Completing the program (making it fit for users and maintainers) involves:

- improving the user interface
- serious work on error handling
- adding a few useful features
- restructuring the code for ease of understanding and modification

## Introduction

When your program first starts running "reasonably", you're probably about half-way finished (if it's a small program).

Here we'll give an example of how real programs evolve under the pressure of requirements and constraints and of how a programmer can gradually improve code.

## Input and output

We can't think of everything all the time, so when we stop to reflect, we find we have forgotten something. Like we forgot about initial requirements for the user interface.

For some tasks, the initial requirements cannot be changed, and that's usually leads to poor solutions.  We think that writing **Expression:** and **Result:** is a bit too "heavy" and distracting. During initial debugging, we added = as a result indicator. We would also like a short "prompt" to indicate that the program wants input, e.g., > character.

```console
> 2+3;
= 5
```
