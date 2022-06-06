---
layout: default
title: Bitwise Operators
has_children: false
---

# Bitwise Operators

{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---



# Bitwise Operators

### AND Operator (&)

```
If two input bits are 1, the output is 1.
In all other cases its 0, for example:
1 & 0 => yields to 0.
0 & 1 => yields to 0.
0 & 0 => yields to 0.
```

### OR Operator (|)

```
If two input bits are 0, the output is 0.
In all other cases, it is 1. For example:
1 | 0 => yields to 1.
0 | 1 => yields to 1.
1 | 1 => yields to 1.
```

### NOT Operator (~)


### XOR Operator (^)

### Shift Operators

These operators can be applied to integral types such as int, long, short, byte, or char.  

There are three types of shift:  

> Left shift: << is the left shift operator and meets both logical and arithmetic shifts’ needs.
> Arithmetic/signed right shift: >> is the arithmetic (or signed) right shift operator.
> Logical/unsigned right shift: >>> is the logical (or unsigned) right shift operator.

In Java, all integer data types are signed and << and >> are solely arithmetic shifts.

```
// Left Shift <<
Here’s an example of a left shift:

6 = 00000110

Shifting this bit pattern to the left one position (6 << 1) results in the number 12:

6 << 1 =00001100

As you can see, the digits have shifted to the left by one position, and the last digit on the right is filled with a zero. Note that shifting left is equivalent to multiplication by powers of 2.

6 << 1
 → 6 * 2^1

6 << 3
 → 6 * 2^3

Well-optimized compilers will use this rule to replace multiplication with shifts whenever possible, as shifts are faster.

With right shift, you can either do arithmetic (>>) or logical (>>>) shift.

The difference is that arithmetic shifts maintain the same most significant bit (MSB) or sign bit, the leftmost bit which determines if a number is positive or negative.

// Signed Right Shift >>

1011 0101>>1 = 1101 1010

x >> y = x/(z^y)​

// unsigned Right Shift >>>

On the other hand, a logical shift simply moves everything to the right and replaces the MSB with a 0.

1011 0101 >>> 1 = 0101 1010

Formula: a >>> b = a/(2^b)
​
```

## Tricks

- Check if a number is even
