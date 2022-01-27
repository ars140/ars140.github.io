---
layout: post
title: Infinity, Divergent Series, and Negative Numbers
author: Alex
tags: []
---

What do these have in common?

## A Series of Events

A couple of months ago, I showed an interesting math fact to my family (it made
sense to bring up in the context, I promise), related to this infinite series:

$$ S = \sum_{i=0}^{\infty} 2^i = 1 + 2 + 4 + 8 + 16 + ...$$

Obviously, this is a divergent series which doesn't have a sum, as it quickly
snowballs to infinity. But we can rearrange this series in an interesting way by
factoring out a 2:

$$S = 1 + 2 * (1 + 2 + 4 + ...)$$

$$S = 1 + 2 * S$$

Rearranging, we find that:

$$S = -1$$

When I showed this to my sister, she compared this "$$S=\infty=-1$$" logic to:

$$Our\ dog = a\ girl$$

$$I = a\ girl$$

$$And\ therefore,\ I = our\ dog$$

And yes, this isn't how infinite series should work. Many would (rightly) call
this an abuse of infinite series. But what I like about this problem is that this
isn't just a mathematical curiosity -- this is exactly how computers store
negative numbers.

## Binary Values

Binary representation (base 2 system, using 0 and 1 as the digits) is how computers store
information, rather than the more familiar decimal (base 10, using 0-9 as the
digits) system that we use every day.

<!-- In the decimal system, the number $$ 123 $$ means that we have one 100, two
10's, and three 1's, or:

$$ 123 = 1 * 100 + 2 * 10 + 3 * 1 $$

Or more generally:

$$ Value = \sum_{i=0}^{N} x_i * 10^i $$

Where $$ x_i $$ can take one of the values 0-9. -->

Here's a couple of examples of integers converted into their equivalent 8-bit
binary representation (note that binary values are prefixed with "$$0b$$" to
represent that they're in binary):

| Decimal Value | Binary Representation (8-bit) |
|---------------|-------------------------------|
| $$ 1   $$     | $$ 0b00000001 $$              |
| $$ 10  $$     | $$ 0b00001010 $$              |
| $$ 123 $$     | $$ 0b01111011 $$              |

An 8-bit binary value represented by the following (where $$ x_i $$ is $$0$$ or
$$1$$):

$$ Value = 0bx_7 x_6 x_5 x_4 x_3 x_2 x_1 x_0 $$

Which is equivalent to:

$$ Value = \sum_{i=0}^{7} x_i * 2^i $$

## Two's Complement Arithmetic

For negative integers, computers commonly use the Two's Complement
representation. This representation makes arithmetic convenient, but requires a
quick conversion:

1. First, take the bitwise representation of the number to negate.
2. Next, flip all the bits to obtain the Ones' Complement representation of the
   negative number.
3. Finally, add $$1$$ to the Ones' Complement representation to obtain the Two's
   Complement representation.

For an example, let's represent $$-1$$ as an 8-bit value in Two's Complement:

| Representation        | Value    |
|-----------------------|----------|
| Decimal               | $$ -1 $$ |
| 1. Positive Binary Value | $$ +1 = 0b00000001 $$ |
| 2. One's Comp (Flip bits of Pos. Value) | $$ -1 = 0b11111110 $$ |
| 3. Two's Comp (Add 1 to One's Comp)     | $$ -1 = 0b11111111 $$ |

<!-- If we represent each bit as a value $$ x_i $$, then we can see that the binary
value
$$ Value = 0bx_7 x_6 x_5 x_4 x_3 x_2 x_1 x_0 $$ really means the following:

$$ Value = x_7 * 2^7 + x_6 * 2^6 + x_5 * 2^5 + x_4 * 2^4 + x_3 * 2^3 + x_2 * 2^2
+ x_1 * 2^1 + x_0 * 2^0 $$

$$ Value = \sum_{i=0}^{N} x_i * 2^i for N-bit rep $$ -->

We can further rearrange this to find:

$$ -1 = 0b11111111 $$

$$ 0b11111111 = 2^7 + 2^6 + ... + 2^1 + 2^0 $$

$$ -1 = \sum_{i=0}^{7} 2^i $$

What we've found here is that our representation of $$ -1 $$ in Two's
Complement, $$ \sum_{i=0}^{7} 2^i $$, is equal to our original infinite series,
$$ S = \sum_{i=0}^{\infty} 2^i $$. Or, more accurately, it's only approximately
equal, as we used an 8-bit representation since most computers aren't able to
store $$\infty$$-bit representations of numbers. But if we did have a perfect
$$\infty$$-bit representation, we'd once again find that:

$$ S = \sum_{i=0}^{\infty} 2^i = -1 $$

And this is the same result that we found from our original manipulation of the
infinite series!

<!-- But what happens if we want a different negative number? Well, to get -5 from
-1, just subtract 4 from -1. So set $$x_2 = 0$$ to subtract 4. And we find that
this is still compatible with the two's complement representation! -->

## In Practice

But there's a potential problem. If we're writing a computer program, and we
have the 8-bit value $$ 0b11111111 $$, how do we know whether this is in Two's
Complement (in which case we should interpret it as $$-1$$) or not (in which
case we should interpret it as $$ 255 $$)? Using the same combination of bits to
represent two different numbers seems like it could have a lot of problems!

The way this is solved in programming languages may seem a bit unsatisfying: we
provide _context_ to say which is the correct representation. For example, in C,
when we create an 8-bit integer, we need to declare whether this is a _signed_
type (positive and negative values can be represented by this type) or
_unsigned_ (non-negative values only) type:

```
#include <stdint.h>

uint8_t short x = 255; // 0b11111111, as an unsigned 8-bit integer
int8_t short x = -1;   // 0b11111111, as a signed 8-bit integer
```

The context provided by the integer's type allows the compiler to know whether
the bit value is meant to represent $$ 255 $$ or $$ -1 $$.

So long story short, $$\infty = -1$$ and this is how computers store negative
numbers.
