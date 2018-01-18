---
layout: post
title:  "Notes about `numpy`"
date:   2018-01-17 11:47:43 -0500
categories: jekyll update
---

Often there are more than one way to achieve something in `numpy`, and it is often unclear if one way is faster than the other. Thus I'd like to start a collection of little `numpy` notes with some performance estimates.

1) Logical operators.
`numpy.logical_or(x,y)` vs simply `(x | y)`, there seems to be no significant difference:
```
In [38]: %timeit np.logical_or(x,y)
1.13 µs ± 146 ns per loop (mean ± std. dev. of 7 runs, 1000000 loops each)

In [39]: %timeit (x | y)
1.12 µs ± 114 ns per loop (mean ± std. dev. of 7 runs, 1000000 loops each)
```
for `x` and `y` of `np.bool` type and of 100 by 100 size.

2) Dealing with `nans`.

Say we have a matrix `z` with some float values and we also have boolean matrix `l`, which would serve us a mask.
We want assign `0.0` to the elements of `z` that are `True` in `l`, so simply `z[l]=0.0`. But let's consider several situations:

`l` is equivalent to `np.isnan(z)` - several solutions:
`nan_to_num`:
```
In [72]: %timeit np.nan_to_num(z)
57.9 µs ± 5.03 µs per loop (mean ± std. dev. of 7 runs, 10000 loops each)
```
the straightforward one, ~3 times faster?!:
```
In [80]: %%timeit
    ...: w = np.copy(z)
    ...: w[np.isnan(z)] = 0.0
16.8 µs ± 2.58 µs per loop (mean ± std. dev. of 7 runs, 10000 loops each)
```
the weird one (still faster than `nan_to_num`):
```
In [73]: %timeit np.where(np.isnan(z), z, np.zeros_like(z))
27.7 µs ± 5.45 µs per loop (mean ± std. dev. of 7 runs, 10000 loops each)
```
And just for reference let's how long it takes to assign in place:
```
In [75]: %timeit z[l] = 0.0
4.45 µs ± 977 ns per loop (mean ± std. dev. of 7 runs, 100000 loops each)
```
Part of the problem seems to be coming from the fact that it takes longer to check to `isfinite` than for `isnan`:
```
In [26]: %%timeit
    ...: w = np.copy(z)
    ...: w[np.isfinite(z)] = 0.0
29.1 µs ± 4.27 µs per loop (mean ± std. dev. of 7 runs, 10000 loops each)
```
But it is still slower than `nan_to_num`.
Bottom line - fancy indexing is really fast!



















