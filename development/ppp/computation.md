# Computation

> "If it doesn't have to produce correct results, I can make it arbitrarily fast." - Gerald M. Weinberg

- [Objectives and tools](#objectives-and-tools)
- [Expressions](#expressions)
- [Statements](#statements)
- [Functions](#functions)
- [Vector](#vector)

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

## Expressions

The most basic building block of programs is an *expression*. An expression computes a value from a number of operands. The simplest expression is simply a literal value, such as 10, 'a', or "Norah".

Names of variables are also expressions. A variable represents the object of which it is the name.

```c++
int length = 20;  	// the rvalue of length - the object named by length
int area = length * 10; // the lvalue of length - the value of the object named by length
```

Sometimes (as an lvalue) **length** refers to the box (object) and sometimes (as an rvalue) **length** refers to the value in that box.

We can make more complicated expressions by combining expressions using operators and parentheses to group expressions.

```c++
int perimeter = (length+width)*2;
```

The usual mathematical rules of operator precedence apply. The first rule for the use of parentheses is simply "If in doubt, parenthesize". Use parentheses sparingly, as their overuse decreases readability.

Ugly code slow downs reading and comprehension. Don't write absurdly complicated expressions and always try to choose meaningful names.

### Constant expressions

Program  typically use a lot of constants. C++ offers the notion of a symbolic constant, a named object to which you can't give a new value after it has been initialized.

```c++
constexpr double pi = 3.14159;
pi = 7;		// error: assignment to constant
```

Such constants are useful for keeping code readable. It's easy to change it once in the code. You should use this tool and avoid magic constants.

In some places, such as **case**, C++ requires a *constant expression*, that is, as expressions with an integer value composed exclusively of constant.

```c++
constexpr int max = 17;
max+2;	// a constant expression
```

A **constexpr** symbolic constant must be given a value that is known at compile time.

```c++
constexpr int max = 100;
int n;
constexpr int c1 = max+7; // OK: c1
constexpr int c2 = n+7;	  // error: we don't know the value of c2
```

C++ offers a second form of constant (a **const**) that initialize a "variable" with a value that is not known at compile time but never changes after initialization.

```c++
int n;
const int c1 = n+7; //OK. but you cannot change value of c1
c1 = 7; 	    // error: c1 is a const
```

### Operators

Most operators are conventional.

|			| Name				| Comment 					|
| --------------------- | ----------------------------- | --------------------------------------------- |
| **f**(**a**)		| function call			| pass **a** to **f** as an argument		|
| ++**lval**		| pre-increment			| increment and use the incremented value	|
| --**lval**		| pre-decrement			| increment and use the incremented value	|
| !**a**		| not				| result is **bool**				|
| -**a**		| unary minus			|						|
| **a**`*`**b** 	| multiply			|						|
| **a**/**b**		| divide			|						|
| **a**%**b**		| modulo (reminder)		|						|
| **a**+**b**		| add				|						|
| **a**-**b**		| subtract			|						|
| **out**<<**b**	| write **b** to **out**	| where **out** is an **ostream**		|
| **in**>>**b**		| read from **in** into **b**	| where **in** is an **istream**		|
| **a**<**b**		| less than			| result is **bool**				|
| **a**<=**b**		| less than or equal		| result is **bool**				|
| **a**>**b**		| greater than			| result is **bool**				|
| **a**>=**b**		| greater than or equal		| result is **bool**				|
| **a**==**b**		| equal				| not to be confused with 			|
| **a**!=**b**		| not equal			| result is **bool**				|
| **a**&&**b**		| logical and			| result is **bool**				|
| **a**||**b**		| logical or			| result is **bool**				|
| **lval** = **a**	| assignment			| not to be confused with ==			|
| **lval** `*=` **a**	| compound assignment		| **lval** = **lval**`*`**a**; also for /,%,+,-	|	

We used **lval** (short for "value that can appear on the left-hand side of an assignment") where the operator modifies an operand.

In general, a way of saying something in a program is better that another if it more directly expresses ad idea. The result is more concise and easier for a reader to understand.

```c++
++a;
a+=1;
```

Here `++a` more directly expresses the idea of incrementing.

Similarly, we prefer `a*=scale` over `a=a*scale`.

### Conversions

We can "mix" different types in expressions. The rule is that if an operator has an operand of type **double**, we use floating-point arithmetic yielding a **double** result; otherwise, we use integer arithmetic yielding an **int** result.

```
5/2 is 2 (not 2.5)
2.5/2 means 2.5/double(2), that is, 1.25
'a'+1 means int{'a'}+1
```

The notation **type(value)** and **type{value}** mean "convert **value** to **type** as if you were initializing a variable of type **type** with the value **value**".

The notation **type{value}** prevents narrowing, but the **type(value)** notation does not.

```c++
double d = 2.5;
int i = 2;

double d2 = d/i;  // d2 == 1.25
int i2 = d/i; 	// i2 == 1
int i3 {d/i};	// error: double -> int conversion may narrow
```

Beware that it is easy to forget about integer division in an expression that also contains floating-point operands.

## Statements

An expression computes a value from a set of operands using some operators.

In C++ you use language constructs called *statements* to express things like:

- producing several values
- repeating something
- choosing among alternatives
- get input or produce output

### Declaration statement

```c++
int a = 7;
```

### Expression statement

An expression statement is simply an expression followed by a semicolon.

```c++
a = b;
++b;
```

In general, we want a statement to have some effect. Thus, expression statements are typically assignments, I/O statements, or function calls.

With not careful placing of semicolon you can create an *empty statement*, a statement doing nothing: 

```c++
if (x == 5);
```

### Selection

#### if-statements

The simplest form of selection is an **if**-statement, which selects between two alternative.

```c++
if(a<b)
    cout << a << " < " << b << "\n";
else
    cout << b << " < " << a << "\n";
```

If its condition is true, the first statement is executed; otherwise, the second statement is.

We tend to make programs assuming that the user enters proper input. It's not always the case, unfortunately.

We must always test our programs with "bad" input. A program should behave sensibly even is its users don't.

The general form of an **if**-statement is

```c++
if (expression)
    statement
else
    statement
```

We can use an **if** statement as the **else** part of an **if**-statement (there is no an "**else-if**-statement" in C++):

```c++
if (expression)
    statement;
else if (expression)
    statement;
else
    statement;
```

In this way, we can write arbitrarily complex tests ans associate a statement with each alternative. However, please remember that one of the ideals for code is simplicity, rather than complexity.

#### switch-statements

The most common form of selection is a selection based on comparison of a value against several constants.

```c++
switch (unit) {
case 'i':
    cout << "something";
    break;
case 'c':
    cout << "another thing";
    break;
default:
    cout << "default thing";
    break;
}
```

The value presented in parentheses after the **switch** is compared to a set of constants. If the value equals the constant in a **case** label, the statement for that case is chosen. Each case is terminated by a **break**. If the value doesn't match any of the **case** labels, the statement identified by the **default** label is chosen (using which is a good practice).

#### Switch technicalities

Some technical details about **switch**-statements:

- The value on which we switch must be of an integer, **char**, or enumeration.
- The values in the **case** labels must be constant expressions. They cannot be variables.
- You cannot use the same value for two **case** labels.
- You can use several **case** labels for a single case.
- Don't forget to end each **case** with a **break**.

Note. To select based on a **string** you have to use an **if**-statement or a **map**.

```c++
char a;

switch (a) {
case '0': case '2': case '4': case '6': case '8':
    cout << "is even\n";
    break;
case '1': case '3': case '5': case '7': case '9':
    cout << "is odd\n";
    break;
default:
    cout << "is not a digit\n";
    break;
}
```

If you will forget to add **break** statement, then you can "drop through" from one case into another, executing statements of both of them.

### Iteration

*Iteration* is we you repeat doing something to a series of elements of a data structure.

#### while-statements

```c++
// calculate and print a table of squares 0-99
int main()
{
    int i = 0;      // start from 0
    while (i<100) {
        cout << i << '\t' << square(i) << '\n';
        ++i;        // increment i (i = i+1)
    }
}
```

- A while-statement is a way to repeat some statement (to loop).
- `int i` here is a *loop variable* or a *control variable* used to keep track of a number of loop iterations. The loop variable for a while-statement must be defined and initialized outside (before) the while-statement.
- An initializer for the loop variable is zero in this example.
- A termination criterion is 100. If control variable is 100, we leave the while-statement and execute what comes next.
- Output statement and increment are the statements to repeat (the *body* of the loop). The loop body is a block (delimited by curly braces).

#### Blocks

A *block* or a *compound statement* is a sequence of statements delimited by curly braces { and }.

The empty block { } is sometimes useful for expression that nothing is to be done.

```c++
if (a<=b) {	// do nothing
}
else {
    int t = a;
    a = b;
    b = t;
}
```

#### for-statements

A for-statement is like a while-statement except that the management of the control variable is concentrated at the top where it is easy to see and understand. Prefer use a for-statement.

```c++
// calculate and print a table of squares 0-99
int main()
{
    for (int i = 0; i<100; ++i)
        cout << i << '\t' << square(i) << '\n';
}
```

Never modify the loop variable inside the body of a for-statement.

There is also a simpler "range-for-loop" for traversing collections of data, such as vectors.

## Functions

A *function* is a named sequence of statements. A function can return a result - a *return value*.

We may not use the result of a function call, but we have to give a function exactly the arguments it requires.

The syntax of a *function definition* is:

```
type identifier ( parameter-list )
function-body
```

The *function body* is the block that actually does the work.

The list of arguments is called a *parameter list* and its elements are called *parameters* (or *formal arguments*). The list of parameters can be empty, and if we don't want to return a result we give `void` (meaning "nothing") as the return type.

```c++
void write_sorry()
{
    cout << "Sorry\n";
}
```

### Why bother with functions?

Functions 

- makes the computation logically separate
- makes the program text clearer
- provides opportunity to reuse functions
- eases testing

Programs are usually easier to write and to understand if each function performs a *single* logical action.

One of the purposes of functions is to simplify code by separating out complicated calculations as named functions.

### Function declarations

Almost all of the time we are just interested in knowing how to call a function - seeing the definition would just be distracting, as we often don't want to look at a function body.

C++ provides a way of supplying that information separate from the complete function definition - a *function declaration*.

```c++
int square(int);
double sqrt(double);
```

Note the terminating semicolons.

So, if you just want to use a function, you simply write - or more commonly `#include` - its declaration. The function definition can be elsewhere.

We use declarations to keep most of the code out of sight to allow us to concentrate on a single part of a program at a time.

## vector

To do just about anything of interest in a program, we need a collection of data to work on.

A `vector` is simply a sequence of elements that you can access by an index.

![vector](img/vector.png)

We refer to an element by subscripting the name of the `vector` with the element's index, so here the value of v[1] is 7. Indices for a `vector` always start with 0 and increase by 1.

A `vector` doesn't just store its elements, it also stores its size.

To make a `vector` we need to specify the type of the elements and the initial set of elements. The element type comes after `vector` in angle brackets (< >).

A `vector` will only accept elements of its declared element type.

```c++
vector<int> v = {5, 7, 9, 4, 6, 8}; // vector of 6 ints
vector<string> philosophers = {"Kant", "Pluto", "Hume", "Kierkegaard"}; // vector of 4 strings
```

We can also define a `vector` of a given size without specifying the element values. The elements are given a default value according to the element type.

```c++
vector<int> vi(6); // vector of 6 ints initialized to 0
vector<string> vs(4); // vector of 4 strings initialized to ""
```

The string with no characters "" is called the *empty string*.

Please note that you cannot refer to a nonexistent element of a `vector`, this will cause run-time error.

### Traversing a `vector`

We can print the elements of a `vector` like this:

```c++
    vector<int> v = {5, 7, 9, 4, 6, 8};
    for (int i=0; i<v.size(); ++i)
        cout << v[i] << '\n';
```

The call `v.size()` gives the number of elements of the `vector` called `v`. The range for a `vector v` is [`0:v.size()`) - the half-open sequence of elements. The first element is `v[0]` and the last `v[v.size()-1]`. If `v.size()==0`, `v` has no elements - an empty `vector`.

You can traverse `vector`'s elements using a range-`for`-loop:

```c++
    vector<int> v = {5, 7, 9, 4, 6, 8};
    for (int x : v)
        cout << x << '\n';
```

### Growing a `vector`

Often, we start a `vector` empty and grow it to its desired size as we read or compute the data we want in it.

The `push_back()` member function of `vector` adds new element to the end of the `vector`.

```
member-function-call:
    object_name.member-function-name ( argument-list)
```

### A numeric example

```c++
// read some temperatures into a vector
// and coumpute mean and median temperatures
int main()
{
    vector<double> temps;
    for (double temp; cin>>temp; )  // read into temp; exit loop if input is not double
        temps.push_back(temp);

    // compute mean temperature:
    double sum = 0;
    for(int x : temps) sum += x;
    cout << "Average temperature: " << sum/temps.size() << '\n';

    // compute median temperature:
    sort(temps);    // median is when half of he values are lower and the other half are higher
    cout << "Median temperature: " << temps[temps.size()/2] << '\n';
}
```

`cin>>temp` is true if a value was read correctly (it's a double) and false otherwise.

We used `for` instead of `while` to limit the scope of input variable `temp`.

### A text example

If you need to analyze data, you'll use `vector` (or a similar data structure).

```c++
// simple dictionary: list of sorted words
int main()
{
    vector<string> words;
    for (string temp; cin>>temp; )  // read whitespace-separated words
        words.push_back(temp);
    cout << "Number of words: " << words.size() << '\n';

    sort(words);

    for (int i = 0; i<words.size(); ++i)
        if (i==0 || words[i-1]!=words[i])
            cout << words[i] << "\n";
}
```

We can stop reading string input by providing "not ordinary" character. In Linux you can terminate as input stream using `Ctrl+D`.

You can compare strings using lexicographical ordering.
