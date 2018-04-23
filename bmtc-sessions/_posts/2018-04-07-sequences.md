---
title: Sequence of Sequences
tags: Sequences, magic squares, lazy caterer's sequence, Floyd's triangle
---

This session was led by Jerod Morehouse of Timberline High School.
We looked at a sequence of sequences:
the magic square numbers,
the lazy caterer's sequence,
and more.

A magic square is an n-by-n square filled with the numbers 1 through n^2,
in such a way that every row, every column, and both of the long diagonals add up to
the same number.
Magic square numbers are the numbers that the rows, columns, and diagonals add up to.
For a 3-by-3 magic square, the rows, columns, and diagonals add up to 15;
for 4-by-4, they add up to 34.
We found a formula for the magic square numbers.
We also found 3-by-3 and 4-by-4 magic squares,
and we read about some rules for constructing larger magic squares.
We also mentioned briefly
<a href="http://www.bradyharanblog.com/the-parker-square/">Parker's square</a>,
an attempted (but incomplete) solution to one of the many variations on the magic square theme.

The <a href="https://en.wikipedia.org/wiki/Lazy_caterer's_sequence">lazy caterer's sequence</a>
is the sequence giving the number of pieces that a disk
(like a pizza) can be cut into after a given number of straight-line cuts.
This sequence starts with 1, 2, 4; but then instead of 8, 16, 32... it continues with
7, 11, 16...
We came up with a formula for this sequence, too.
And we came up with a couple of different ways to understand the formula and why it works,
including recursive reasoning and identifying a polynomial based on successive differences.

Next we looked at a variation of the lazy caterer's sequence: the number of pieces
that a "donut" can be cut into after a given number of straight-line, vertical cuts.
In other words, this is the number of pieces that an annulus (ring-shaped planar region)
can be divided into.
This sequence starts with 2, 5, 9, 14...
Again we came up with a formula for this sequence.

We closed with looking at <a href="https://en.wikipedia.org/wiki/Floyd%27s_triangle">Floyd's triangle</a>,
an arrangement of the natural numbers that reveals both of the lazy caterer sequences
and also the triangular numbers, along the triangle's diagonals and columns.
And the magic square numbers also appear as the row sums of Floyd's triangle!
It was impressive to see all these sequences packaged together into one neat triangle.

## Handout from the session

{% include handouts.html %}

<br />

<small>
(Header image: This <a href="https://www.wikipedia.org/">Wikipedia</a>
and <a href="https://commons.wikimedia.org/">Wikimedia Commons</a> image is from the user
<a href="https://en.wikipedia.org/wiki/User:Chris_73">Chris 73</a> and is freely available at
<a href="https://commons.wikimedia.org/wiki/File:NautilusCutawayLogarithmicSpiral.jpg">https://commons.wikimedia.org/wiki/File:NautilusCutawayLogarithmicSpiral.jpg</a>
under the <a href="https://creativecommons.org/licenses/by-sa/3.0/">creative commons cc-by-sa 3.0</a> license.)
</small>
