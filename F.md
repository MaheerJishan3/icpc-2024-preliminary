# F. Three Quick Brown Foxes Jump Over a Lazy Chicken

## Problem Summary

Three clever foxes are tasked with catching a cautious chicken that roams freely within a triangular field, which is fenced on all sides.
Each fox guards one side of the triangle and must find an optimal position along their respective side to set a trap inside the triangle.
The goal is for all three foxes to jump to the trap simultaneously, covering the shortest possible distance while maintaining the same speed.
The foxes cannot position themselves at the triangle's vertices and must ensure that no two foxes occupy the same side.

The challenge is to determine the shortest jump distance required for the foxes to reach the trap, given the lengths of the triangle's sides.
The input consists of multiple test cases, each providing the lengths of the three sides of the triangle. The output for each test case should be the square of the shortest jump distance expressed as an irreducible fraction.

## Solution

### Thought Process

The foxes are on the sides of the triangle and we have to figure out same shortest distance from all sides of a triangle.
The shortest distance inside a triangle is in the center. In other words, if we draw a circle inside the triangle, the radius of the circle is the shortest distance.

First we have to find the perimeter of the triangle with this formula: `a + b + c` where a, b & c are the length of the sides

After that we have to find the Area of the triangle with this formula: $\sqrt{s * (s-a) * (s-b) * (s-c)}$ | where <code>s = perimeter / 2</code>

Lastly we have to stylize the output: the result would be square of the shortest jump distance expressed as an [irreducible fraction](https://en.wikipedia.org/wiki/Irreducible_fraction).

Suppose the result is 32. Irreducible fraction result would be $32/1$

To achieve this in our solution we have used Python's `Fraction` library

### Code
```python
import math
from fractions import Fraction

tests = int(input())

for i in range(tests):
    [a, b, c] = input().split(" ")
    a = int(a)
    c = int(c)
    b = int(b)

    perimeter = (a + b + c)
    s = perimeter / 2
    area = math.sqrt(s * (s-a) * (s-b) * (s-c))

    radius = (2 * area) / (perimeter)

    result = Fraction(radius ** 2).limit_denominator()
    print(f"{result.numerator}/{result.denominator}")
```
