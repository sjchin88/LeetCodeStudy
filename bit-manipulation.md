# Bit Manipulation

## Main Operations

<table><thead><tr><th width="125">Symbol</th><th width="144.33333333333331">Operation </th><th>Effect</th></tr></thead><tbody><tr><td>~</td><td>not</td><td>0 -> 1, 1 -> 0</td></tr><tr><td>|</td><td>or</td><td></td></tr><tr><td>&#x26;</td><td>and</td><td></td></tr><tr><td>^</td><td>xor</td><td>0 + 1 -> 1, 1 + 1 -> 0, 0 + 0 -> 0</td></tr><tr><td>&#x3C;&#x3C;</td><td>shift left</td><td></td></tr><tr><td>>></td><td>shift right</td><td></td></tr></tbody></table>



Note:&#x20;

Python bin() built-in function return 0b + bit representation of a number

Python \~ work on signed int, so directly use \~ to find the invert of 1 bit will yield unexpected result, try use a ^ \~ a or a + \~ a instead.

Negative numbers are written with a leading one instead of a leading zero.

Python doesn't use 8-bit numbers. It USED to use however many bits were native to your machine, but since that was non-portable, it has recently switched to using an INFINITE number of bits. Thus the number -5 is treated by bitwise operators as if it were written "...1111111111111111111011".

If we keep on shifting the negative number to the right, we will end up with 11111.... eventually

[https://wiki.python.org/moin/BitwiseOperators](https://wiki.python.org/moin/BitwiseOperators)

## Two-complements

From Wiki

[https://en.wikipedia.org/wiki/Two%27s\_complement](https://en.wikipedia.org/wiki/Two's\_complement)

* How to get / isolate the rightmost 1-bit : `x & (-x)`.
* How to turn off (= set to 0) the rightmost 1-bit : `x & (x - 1)`.

