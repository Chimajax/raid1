```go id="6j0zj9"
package piscine

import "github.com/01-edu/z01"

func QuadB(x, y int) {
	if x <= 0 || y <= 0 {
		return
	}

	for i := 1; i <= y; i++ {
		for j := 1; j <= x; j++ {

			if i == 1 && j == 1 {
				z01.PrintRune('/')

			} else if i == 1 && j == x {
				z01.PrintRune('\\')

			} else if i == y && j == 1 {
				z01.PrintRune('\\')

			} else if i == y && j == x {
				z01.PrintRune('/')

			} else if i == 1 || i == y || j == 1 || j == x {
				z01.PrintRune('*')

			} else {
				z01.PrintRune(' ')
			}
		}
		z01.PrintRune('\n')
	}
}
```

---

# Goal of the program

The function draws rectangles like this:

```text id="5lx8j5"
/***\
*   *
\***/
```

using:

* `/` and `\` for corners
* `*` for borders
* spaces inside

---

# 1. Package declaration

```go id="w7l0fh"
package piscine
```

This tells Go that the file belongs to the `piscine` package.

---

# 2. Importing z01

```go id="m4tijm"
import "github.com/01-edu/z01"
```

The `z01` package is used to print characters one at a time.

Example:

```go id="f5jv8x"
z01.PrintRune('A')
```

prints:

```text id="vr6ztf"
A
```

---

# 3. Function declaration

```go id="0f9scn"
func QuadB(x, y int)
```

This creates a function named `QuadB`.

Parameters:

* `x` → width
* `y` → height

Example:

```go id="0jnh2j"
QuadB(5, 3)
```

means:

* width = 5 columns
* height = 3 rows

---

# 4. Checking invalid sizes

```go id="ot4qv7"
if x <= 0 || y <= 0 {
	return
}
```

If width or height is:

* 0
* negative

the function stops immediately.

So:

```go id="eglt8m"
QuadB(-1, 5)
```

prints nothing.

---

# 5. Outer loop → rows

```go id="b9x3yv"
for i := 1; i <= y; i++ {
```

This loop controls the rows.

If `y = 3`, then:

```text id="7r5j7w"
i = 1
i = 2
i = 3
```

`i` represents the current row.

---

# 6. Inner loop → columns

```go id="r7jz9g"
for j := 1; j <= x; j++ {
```

This loop controls columns inside each row.

If `x = 5`, then:

```text id="vbz97e"
j = 1
j = 2
j = 3
j = 4
j = 5
```

`j` represents the current column.

---

# 7. Understanding coordinates

Every position has coordinates:

```text id="w6a9v4"
(row,column)
```

For `QuadB(5,3)`:

```text id="cqj6e0"
(1,1) (1,2) (1,3) (1,4) (1,5)
(2,1) (2,2) (2,3) (2,4) (2,5)
(3,1) (3,2) (3,3) (3,4) (3,5)
```

The code checks each coordinate and decides what character to print.

---

# 8. Top-left corner

```go id="fph0zd"
if i == 1 && j == 1 {
	z01.PrintRune('/')
}
```

This means:

* first row
  AND
* first column

So coordinate:

```text id="xodrjh"
(1,1)
```

prints:

```text id="s3jdjj"
/
```

---

# 9. Top-right corner

```go id="7wl2i4"
else if i == 1 && j == x {
	z01.PrintRune('\\')
}
```

This means:

* first row
  AND
* last column

For width 5:

```text id="uvq4g0"
(1,5)
```

prints:

```text id="txgvc7"
\
```

---

# 10. Bottom-left corner

```go id="oky6g8"
else if i == y && j == 1 {
	z01.PrintRune('\\')
}
```

This means:

* last row
  AND
* first column

For height 3:

```text id="t1y4c3"
(3,1)
```

prints:

```text id="bj9mnn"
\
```

---

# 11. Bottom-right corner

```go id="h74x4i"
else if i == y && j == x {
	z01.PrintRune('/')
}
```

This means:

* last row
  AND
* last column

Coordinate:

```text id="5xq4zz"
(3,5)
```

prints:

```text id="uwl2rt"
/
```

---

# 12. Borders

```go id="k2f8ye"
else if i == 1 || i == y || j == 1 || j == x {
	z01.PrintRune('*')
}
```

This checks if we are on ANY border.

## Meaning

### Top border

```go id="k5e6y8"
i == 1
```

### Bottom border

```go id="g3azq2"
i == y
```

### Left border

```go id="w92b5f"
j == 1
```

### Right border

```go id="d7bcl5"
j == x
```

The `||` means OR.

So if any of these are true, print:

```go id="u7hf5v"
'*'
```

---

# 13. Inside the rectangle

```go id="0kpbpf"
else {
	z01.PrintRune(' ')
}
```

If the position is not:

* a corner
* a border

then it must be inside.

So we print a space.

---

# 14. New line after each row

```go id="drr8cq"
z01.PrintRune('\n')
```

After finishing one row, move to the next line.

Without this, everything would print on one line.

---

# Full walkthrough for `QuadB(5,3)`

## Row 1

Coordinates:

```text id="ce0mza"
(1,1) → /
(1,2) → *
(1,3) → *
(1,4) → *
(1,5) → \
```

Result:

```text id="ev03w2"
/***\
```

---

## Row 2

```text id="5n9zj3"
(2,1) → *
(2,2) → space
(2,3) → space
(2,4) → space
(2,5) → *
```

Result:

```text id="1v4zqh"
*   *
```

---

## Row 3

```text id="ydg6dg"
(3,1) → \
(3,2) → *
(3,3) → *
(3,4) → *
(3,5) → /
```

Result:

```text id="w0z1pw"
\***/
```

---

# Final output

```text id="gfg54m"
/***\
*   *
\***/
```
