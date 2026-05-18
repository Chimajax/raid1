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
ABBBC
B   B
ABBBC
```

---

**QuadD**

Uses different corner letters depending on position.

Example:

```text id="5qdu4r"
ABBBC
B   B
CBBBA
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
x and y are integers that represent the number of rows and column the input will take,
which will determine the order of what will be printed

* x: The Number of rows to be printed
* y: The number of columns to be printed

