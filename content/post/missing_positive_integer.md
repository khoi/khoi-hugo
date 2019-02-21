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

## Test cases

[4_missing_positive_integer.go](https://github.com/khoi/daily-coding-problem-in-go/blob/master/4_missing_positive_integer.go)

```go
{{< readfileraw file="/content/daily-coding-problem-in-go/4_missing_positive_integer_test.go" >}}
```

## Solution

[4_missing_positive_integer.go](https://github.com/khoi/daily-coding-problem-in-go/blob/master/4_missing_positive_integer.go)

```go
{{< readfileraw file="/content/daily-coding-problem-in-go/4_missing_positive_integer.go" >}}
```
