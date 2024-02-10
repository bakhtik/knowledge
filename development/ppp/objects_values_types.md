# Objects, Types, and Values in C++

> "Fortune favors the prepared mind." - Louis Pasteur

## Input

Real programs tend to produce results based on some input we give them.

An *object* is a region of memory with a *type* that specifies what kind of information can be placed in it.

A named object is called a *variable*.

You can think of an object as a "box" into which you can out a value of the object's type:

![object's box representation](img/box.png)

```c++
// read and write a first name
#include "../std_lib_facilities.h"

int main()
{
    cout << "please enter your first name (followed by 'enter'):\n";
    string first_name;  // first_name is a variable of type string
    cin >> first_name;  // read characters into first_name
    cout << "Hello, " << first_name << "!\n";
}
```

A *prompt* message prompts the user to take an action.

A *definition* is a statement that introduces a new name into a program and sets aside memory for a variable.

```c++
int age;
string first_name;
```

The name `cin` refers to the standard input stream ("see-in", for "character input") defined in the standard library.

The `>>` operator specifies where the input goes. 

Until a newline is entered (the Enter key is hit), the computer simply collects characters. The newline *will not be* part of the string stored in memory.

We use quotes when we want a literal string. When we don't use quote, we refer to the value of something with a name.

## Variables

- *objects*: the "places" in which we store data
- *variable*: a named object that has specific *type*
- *type*: (**int** or **string**) determines what can be put into the object (**123**, or **"Hello"**) and which operations can be applied (multiplication for **int**s, or concatenation for **string**s)
- *values*: the data items we put into variables
- a *definition*: a statement that defines a variable

You cannot put values of the wrong type into a variable - compiler will issue an error during the compilation process.

The most common set of C++ types:

```c++
int number_of_steps = 39;   // int for integer
double flying_time = 3.5;   // double for floating-point numbers
char decimal_point = '.';   // char for individual characters
string name = "Annamarie";  // string for characters strings
bool tap_on = true;         // bool for logical variables
```

Note that each of these types has its own characteristic style of literals.

## Input and type

The input operation `>>` ("get from") is sensitive to type; that is, it reads according to the type of variable you read into.

```c++
string first_name;
int age;
cin >> first_name;  // read a string
cin >> age;         // read an integer
```

By convention, reading of strings is terminated by what is called *whitespace* (space, newline, and tab characters); that is, it reads a *single* word.

Whitespace by default is ignored by `>>`.
You can read several words using `>>` twice or more times:

```c++
string first;
string second;
cin >> first >> second;
```

If you didn't give a variable an initial value, you get some "garbage value" that happened to bi in that part of memory when you started executing.

You can read several values in a single input statement, just as write several values in a single output statements:

```c++
cin >> first_name >> age;
cout << first_name << age;
```

The `<<` operator is sensitive to type, just as `>>`, so we can output variables and literals of different types.

## Operations and operators

Type of a variable determines what operations we can apply to it and what they mean.

```c++
int count;
string name;

int c2 = count + 2;         // + add integers
string s2 = name + " Jr";   // + appends characters
```

The compiler knows exactly which operations can be applied to each variable and can prevent mistakes. But the compiler doesn't know which operations make sense.

### Useful operators for common types

|                   | bool | char | int | double | string |
| ----------------- | ---- | ---- | --- | ------ | ------ |
| assignment        | = | = | = | = | = |
| addition          | | | + | + | |
| concatenation     | | | | | + | 
| subtraction       | | | - | - | | 
| multiplication    | | | * | * | |
| division          | | | / | / | |
| remainder (modulo)| | | % | % | |
| increment by 1    | | | ++ | ++ | |
| decrement by 1    | | | -- | -- | |
| increment by n    | | | += n | += n | |
| add to end        | | | | | += |
| decrement by n        | | | -= n | -= n | |
| multiply and assign   | | | `*=` | `*=` | |
| divide and assign     | | | /= | /= | |
| reminder and assign   | | | %= | | |
| read from s into x    | `s>>x` | `s>>x` | `s>>x` | `s>>x` | `s>>x` |
| write x to s          | `s<<x` | `s<<x` | `s<<x` | `s<<x` | `s<<x` |
| equals                | == | == | == | == | == |
| no equal              | != | != | != | != | != |
| greater than          | >  | >  | >  | >  | >  |
| greater than or equal | >= | >= | >= | >= | >= |
| less than             | <  | <  | <  | <  | <  |
| less than or equal    | <= | <= | <= | <= | <= |

