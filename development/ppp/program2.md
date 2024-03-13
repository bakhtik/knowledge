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

We can get it by a minor change to the main loop of `main()`:

```c++
double val = 0;
while (cin) {
    cout << "> ";               // print prompt
    Token t = ts.get();

    if (t.kind == 'q') break;
    if (t.kind == ';')
	cout << "=" << val << '\n'; // print result
    else
	ts.putback(t);
    val = expression();
```

The result is

```console
> 2+3; 5*7; 2+9;
= 5
> = 35
> = 11

```

We have to mess with `Token_stream` to make this improvement. For now we decide that what we have is good enough.

It is unwise to make major structural changes to gain a minor advantage.

## Error handling

The first thing to do once you have a program that "basically works" is to try to break it; that is, we try to feed it input in the hope of getting it to misbehave. The right attitude when testing is "I'll break it!".

Technically, this is known as *testing*. You shall approach testing seriously. You try to create test cases systematically, and just in case your strategy for selecting tests isn't complete, you do some "unreasonable" tests.
