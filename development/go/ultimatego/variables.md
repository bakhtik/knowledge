# Variables

## Type

Type is life.

Type represents:

- the amount of memory we are reading and writing
- what that memory represents

Basic unit of memory in Go is byte (8 bits).
Until you say what type represent some byte in a memory, it's just an arbitrary set of bits.

```go
	// Declare variables that are set to their zero value.
	var a int
	var b string
	var c float64
	var d bool
```

`float64` shows exactly that the occupied memory is 64 bits or 8 bytes long.

The most efficient integer is based on the architecture you're running on. That's we prefer to use `int` instead of using precise `int8`, `int16`, `int32`, or `int64` and let the compiler to choose most efficient type based on the underlying architecture.

For example, on 32-bit architecture, `int32` is most efficient, likewise, on 64-bit architecture - `int64`. Same for the address scheme and words size.

A **word** is a generic allocation, in case of 32-bit architecture it is a four bytes allocation, in case of 64-bit architecture it's an eight bytes allocation, and it can represent either integer or an address.

*Zero value* means that the compiler will initialize the variable for us to it's type zero value.

For convention, when you use `var` keyword, you basically denotes that that variable stats with zero value.

String type is a two words value, where the first word is a pointer to the string, and the second value is a number of bytes in the string. In case of string zero value, it's first word will have a pointer value of `nil`, and a second word will equal to 0.

If we want to initialize the variable with some value at the point of its declaration we can use the shot variable declaration operator.

```go
	// Declare variables and initialize.
	// Using the short variable declaration operator.
	aa := 10
	bb := "hello"
	cc := 3.14159
	dd := true
```

Use `var` for variables with zero value and short declaration to initialize variable with some non-zero value. Thus you'll make your code much more consistent and readable.

## Conversion over casting

Casting is then you initially allocated some memory (say, one byte integer) and then you pretend that the consequent memory regions are part of the variable (say, you read another three bytes after the original allocated memory spot, assuming a four byte integer). This is quite dangerous operation.

Conversion in contrast is actual allocation of needed amount of memory and moving initial value to that new part of memory. This kind of operation is much more safer.

```go
	// Specify type and perform a conversion.
	aaa := int32(10)

	fmt.Printf("aaa := int32(10) %T [%v]\n", aaa, aaa)
```
