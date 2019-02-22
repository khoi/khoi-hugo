+++
title = "Daily Coding Problem #5 - Higher Order Function"
date = "2019-02-22T20:08:19+07:00"
draft = false
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

## Solution

This one is relatively easy, as long as you're familiar with the idea of higher order function. 

[5_higher_order_function.go](https://github.com/khoi/daily-coding-problem-in-go/blob/master/5_higher_order_function.go)

```go
{{< readfileraw file="/content/daily-coding-problem-in-go/5_higher_order_function.go" >}}
```

## Test case

[5_higher_order_function_test.go](https://github.com/khoi/daily-coding-problem-in-go/blob/master/5_higher_order_function_test.go)

```go
{{< readfileraw file="/content/daily-coding-problem-in-go/5_higher_order_function_test.go" >}}
```


