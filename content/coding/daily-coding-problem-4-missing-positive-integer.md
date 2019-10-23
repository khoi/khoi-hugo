+++
title = "Daily Coding Problem #4 - Missing Positive Integer"
date = "2019-02-21T21:33:55+07:00"
draft = false
categories = ["Daily Coding Problem"]
+++

## Problem

This problem was asked by Stripe.

Given an array of integers, find the first missing positive integer in linear time and constant space. In other words, find the lowest positive integer that does not exist in the array. The array can contain duplicates and negative numbers as well.

For example, the input [3, 4, -1, 1] should give 2. The input [1, 2, 0] should give 3.

You can modify the input array in-place.

## Thoughts

The first solution that comes to mind is:

- Build a dictionary of all positive integers value of the array. This is done in O(n)
- From that dictionary, get the first missing positive integer. That's our result.

However, this doesn't work since the algorithm has to be done using a `constant space` of memory. Thus we have to think of something better.

The problem states that **You can modify the input array in-place.**, this has to be a clue.

So here is the new plan:

- the `result` must be between 1 and `len(arr) + 1`, we can ignore all other values.
- we'll use the array's indices to keep track of all the positive numbers
- iterate through each index of the array, and swap `arr[i]` with `arr[arr[i] + 1]`, and keep swapping until we found a valid value for the index `i`.
- after the operation, we'll end up with an array where all positive numbers are grouped at the beginning of the array.
- we then iterate again and find the first number that doesn't belong, that's our value.

## Test cases

[4_missing_positive_integer_test.go](https://github.com/khoi/daily-coding-problem-in-go/blob/master/4_missing_positive_integer_test.go)

```go
{{< readfileraw file="/content/daily-coding-problem-in-go/4_missing_positive_integer_test.go" >}}
```

## Solution

[4_missing_positive_integer.go](https://github.com/khoi/daily-coding-problem-in-go/blob/master/4_missing_positive_integer.go)

```go
{{< readfileraw file="/content/daily-coding-problem-in-go/4_missing_positive_integer.go" >}}
```
