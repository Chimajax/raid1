```go id="d5q0v7"
package piscine

import "github.com/01-edu/z01"

func QuadC(x, y int) {
	if x < 0 || y < 0 {
		return
	}

	for i := 1; i <= y; i++ {
		for j := 1; j <= x; j++ {
			if (i == 1 && j == 1) {
				z01.PrintRune('A')
			} else if (i == 1 && j == x) {
				z01.PrintRune('A')
			} else if (i == y && j == 1) {
				z01.PrintRune('C')
			} else if (i == y && j == x) {
				z01.PrintRune('C')
			} else if i == 1 || i == y {
				z01.PrintRune('B')
			} else if j == 1 || j == x {
				z01.PrintRune('B')
			} else {
				z01.PrintRune(' ')
			}
		}
		z01.PrintRune('\n')
	}
}
```

---

# What this program does

This function draws rectangles like this:

```text id="3w3thx"
ABBBA
B   B
CBBBC
```

using:

* `A` for the top corners
* `C` for the bottom corners
* `B` for borders
* spaces inside

---

# 1. Package declaration

```go id="8q5tl4"
package piscine
```

This tells Go that the file belongs to the `piscine` package.

---

# 2. Importing z01

```go id="1p2r1o"
import "github.com/01-edu/z01"
```

The `z01` package is used to print characters one at a time.

Example:

```go id="kl4eqt"
z01.PrintRune('A')
```

prints:

```text id="s5p3z7"
A
```

---

# 3. Function declaration

```go id="r81m0t"
func QuadC(x, y int)
```

This creates a function named `QuadC`.

Parameters:

* `x` → width
* `y` → height

Example:

```go id="a7p4o0"
QuadC(5, 3)
```

means:

* width = 5 columns
* height = 3 rows

---

# 4. Checking invalid values

```go id="gwd1ey"
if x < 0 || y < 0 {
	return
}
```

If width or height is negative, the function stops.

Example:

```go id="5b7kcg"
QuadC(-2, 5)
```

prints nothing.

---

# Important note

You used:

```go id="9mq5we"
x < 0 || y < 0
```

This allows:

```go id="l1z1qf"
QuadC(0, 5)
```

The loops will simply not run because `j <= x` becomes `j <= 0`.

Most projects usually use:

```go id="pabqyn"
x <= 0 || y <= 0
```

to reject zero too.

---

# 5. Outer loop → rows

```go id="0lk5qv"
for i := 1; i <= y; i++ {
```

This loop controls rows.

If `y = 3`:

```text id="cdp9to"
i = 1
i = 2
i = 3
```

`i` represents the current row.

---

# 6. Inner loop → columns

```go id="f8l0yu"
for j := 1; j <= x; j++ {
```

This loop controls columns.

If `x = 5`:

```text id="j2tw6k"
j = 1
j = 2
j = 3
j = 4
j = 5
```

`j` represents the current column.

---

# 7. Coordinates

Every position has coordinates:

```text id="z7kpao"
(row,column)
```

For `QuadC(5,3)`:

```text id="qf8h5d"
(1,1) (1,2) (1,3) (1,4) (1,5)
(2,1) (2,2) (2,3) (2,4) (2,5)
(3,1) (3,2) (3,3) (3,4) (3,5)
```

The program checks each coordinate and decides what character to print.

---

# 8. Top-left corner

```go id="3ehp0q"
if (i == 1 && j == 1)
```

This means:

* first row
  AND
* first column

Coordinate:

```text id="1tfqz9"
(1,1)
```

prints:

```go id="ebv8r8"
z01.PrintRune('A')
```

So the top-left corner becomes:

```text id="5g5uhg"
A
```

---

# 9. Top-right corner

```go id="8ef3yf"
else if (i == 1 && j == x)
```

This means:

* first row
  AND
* last column

For width 5:

```text id="n1zsl6"
(1,5)
```

prints:

```text id="1cddyb"
A
```

So both top corners are `A`.

---

# 10. Bottom-left corner

```go id="68tb2x"
else if (i == y && j == 1)
```

This means:

* last row
  AND
* first column

For height 3:

```text id="3t8mho"
(3,1)
```

prints:

```text id="zq1m7t"
C
```

---

# 11. Bottom-right corner

```go id="h9x3d8"
else if (i == y && j == x)
```

This means:

* last row
  AND
* last column

Coordinate:

```text id="wmt9cb"
(3,5)
```

prints:

```text id="k04mjk"
C
```

So both bottom corners are `C`.

---

# 12. Top and bottom borders

```go id="gw7gkk"
else if i == 1 || i == y
```

This checks:

* first row
  OR
* last row

These are horizontal borders.

The program prints:

```go id="otgby4"
z01.PrintRune('B')
```

So:

```text id="a9f2i0"
ABBBA
```

has `B` characters between the corners.

---

# 13. Left and right borders

```go id="t8k22k"
else if j == 1 || j == x
```

This checks:

* first column
  OR
* last column

These are vertical borders.

The program prints:

```go id="w7o5o4"
B
```

Example:

```text id="4jfw9z"
B   B
```

---

# 14. Inside the rectangle

```go id="rn8i6o"
else {
	z01.PrintRune(' ')
}
```

If the position is not:

* a corner
* a border

then it is inside the rectangle.

So we print spaces.

---

# 15. New line after each row

```go id="u8wwfc"
z01.PrintRune('\n')
```

After finishing one row, move to the next line.

Without this, everything would print on one line.

---

# Full walkthrough for `QuadC(5,3)`

## Row 1

```text id="95h09f"
(1,1) → A
(1,2) → B
(1,3) → B
(1,4) → B
(1,5) → A
```

Result:

```text id="91rrgo"
ABBBA
```

---

## Row 2

```text id="3t8qyu"
(2,1) → B
(2,2) → space
(2,3) → space
(2,4) → space
(2,5) → B
```

Result:

```text id="v2r3qa"
B   B
```

---

## Row 3

```text id="0bbq2g"
(3,1) → C
(3,2) → B
(3,3) → B
(3,4) → B
(3,5) → C
```

Result:

```text id="3s8vvq"
CBBBC
```

---

# Final output

```text id="g7e0v6"
ABBBA
B   B
CBBBC
```
