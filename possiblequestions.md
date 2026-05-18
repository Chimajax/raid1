# Possible Questions for Raid 1

Please Note that these are the possible questions and answer for the Raid,
this doesnt actually determine the actual questions that will be asked.

---

This Page will be deleted soon

---
## First Step: Understand your Code

This is reequired, you should understand your code, then this will help prepare for some questions

## Questions

### What is the for Loop for?

A for loop is used when we want to repeat something multiple times without writing the same code again and again.

Simple example:

Instead of writing:
```go
fmt.Println("Hello")
fmt.Println("Hello")
fmt.Println("Hello")
fmt.Println("Hello")
fmt.Println("Hello")
```

We write
```go
for i := 1; i <= 5; i++ {
	fmt.Println("Hello")
}
```

In your `Quad` functions, loops are used because the program must repeat work:

* row by row
* column by column

### what happends when we use 2 `for` loops
Note: When a loop is inside another loop, it is called a:

`nested loop`

Example:

```go

for i := 1; i <= 3; i++ {      // outer loop
	for j := 1; j <= 5; j++ {  // inner loop

	}
}

```

The first loop is the outer loop
The loop inside it is the inner loop

In QuadA:

* outer loop handles → rows
* inner loop handles → columns

### What is the Difference Between Quad C, D & E

The main difference between `QuadC`, `QuadD`, and `QuadE` is the **characters used for the corners and borders**.

They all:

* use loops the same way
* draw rectangles the same way
* check rows and columns similarly

What changes is the design/style of the rectangle.

---

**QuadC**

Uses:

* `A` and `C` for corners
* `B` for borders

Example:

```text id="b6f9tw"
ABBBA
B   B
CBBBC
```

---

**QuadD**

Uses different corner letters depending on position.

Example:

```text id="5qdu4r"
ABBBC
B   B
ABBBC
```

Top corners and bottom corners are reversed compared to QuadC.

---

**QuadE**

Another variation of corner placement.

Example:

```text id="z6h2nh"
ABBBC
B   B
CBBBA
```

But the corner logic changes depending on:

* top-left
* top-right
* bottom-left
* bottom-right

So QuadE has more detailed corner conditions.

---

In short:

| Quad  | Difference                  |
| ----- | --------------------------- |
| QuadC | Simple A/C corners          |
| QuadD | Opposite corner arrangement |
| QuadE | More specific corner rules  |

The looping structure is almost identical in all of them.


### What is x and y in Quad(x, y)
x and y are `integers` that represent the number of rows and column the input will take,
which will determine the order of what will be printed

* x: The Number of columns to be printed
* y: The number of rows to be printed

### What is `&&` and `||`

* && : This represents `and` command - it requires both statement to be correct,
* || : This represents the `or` command - it requires at least one statement to be correct as the name implies - the way the english word OR is used

 THEY can be used when passing the functions 

 example:
 ```go
if (x <= 0 || y <= 0) {
	return
}
```
this means if x is 0 OR y is 0, return nothing

 
 ```go
if (x <= 0 && y <= 0) {
	return
}
```
this means if x is 0 AND y is 0, return nothing

> an empty "return" means return nothing


### What is package `piscine`

`package piscine` means the file belongs to a group of Go code called `piscine`.

A package helps organize related functions and files together.

Example:

```go id="9r6v9y"
package piscine
```

tells Go:

> “This file is part of the `piscine` package.”

So functions like:

```go id="wjaxph"
QuadA()
QuadB()
```

can all belong to the same package and work together.

### What is go.mod

`go.mod` is the main file that manages a Go project.

It tells Go:

the project name
* which Go version is used
* which external packages the project needs

Example:
```mod
module myproject

go 1.22
```

### What is go.sum
go.sum

go.sum stores security/check information for downloaded packages.

It helps Go verify:

> “Did this package change or get corrupted?”

Go creates it automatically.

### What is the import z01 link?

`"github.com/01-edu/z01"`

This is an external Go package/library.

> import "github.com/01-edu/z01"

It comes from GitHub and provides useful functions.

In your project, it is mainly used for:

```go

z01.PrintRune('A')
```

which prints one character (rune) at a time.

### What is the Difference between `=` and `==`

# `=`

Assignment operator.

Used to give/change a value.

Example:

```go id="ry0g8v"
x = 5
```

means:

> put 5 into `x`

---

# `==`

Comparison operator.

Used to check if two values are equal.

Example:

```go id="v1h4e6"
x == 5
```

means:

> is `x` equal to 5?

It returns:

* `true`
* or `false`

---

# `:=`

Short variable declaration.

Used to create and assign a variable at the same time.

Example:

```go id="jxukw4"
x := 5
```

means:

> create `x` and store 5 in it

---

Simple summary:

| Symbol | Meaning                  |
| ------ | ------------------------ |
| `=`    | assign/change value      |
| `==`   | compare values           |
| `:=`   | create + assign variable |


### What is i++

it means `i = i + 1` it is used to add a value to the `for` loop

### Why use `x <= 0 || y <= 0` and `return`

We use:
```go

x <= 0 || y <= 0
```

to check for invalid rectangle sizes.
A rectangle cannot have:

* zero width
* zero height
* negative size

So if either value is invalid, the function stops:

return

Example:
```go

QuadA(0, 5)
```

or
```go
QuadA(-3, 2)
```

should print nothing because those sizes do not make sense for drawing a rectangle.


