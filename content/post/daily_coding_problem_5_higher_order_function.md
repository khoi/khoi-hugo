+++
title = "Daily Coding Problem #5 - Higher Order Function"
date = "2019-02-22T20:08:19+07:00"
draft = true
categories = ["Daily Coding Problem"]
+++

## Problem

This problem was asked by Jane Street.

`cons(a, b)` constructs a pair, and `car(pair)` and `cdr(pair)` returns the first and last element of that pair. For example, `car(cons(3, 4))` returns 3, and `cdr(cons(3, 4))` returns 4.

Given this implementation of cons:

```python
def cons(a, b):
    def pair(f):
        return f(a, b)
    return pair
```

Implement `car` and `cdr`.
