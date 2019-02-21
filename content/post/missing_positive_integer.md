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
package daily_coding_problem_in_go

import "testing"

var missingPositiveIntTests = []struct {
	in  []int
	out int
}{
	{[]int{3, 4, -1, 1}, 2},
	{[]int{1, 2, 0}, 3},
	{[]int{1, 2, 3}, 4},
	{[]int{3, 2, 1}, 4},
	{[]int{-1, 4, 2, 3, 1}, 5},
}

func TestMissingPositiveInt(t *testing.T) {
	for _, tc := range missingPositiveIntTests {
		dup := make([]int, len(tc.in)) // dupe it since we modify the input in-place
		copy(dup, tc.in)
		if actual := MissingPositiveInt(tc.in); actual != tc.out {
			t.Errorf("%v, expecting %v, got %v", dup, tc.out, actual)
		}
	}
}
```

## Solution

[4_missing_positive_integer.go](https://github.com/khoi/daily-coding-problem-in-go/blob/master/4_missing_positive_integer.go)

```go
package daily_coding_problem_in_go

func MissingPositiveInt(arr []int) int {
	for i, e := range arr {
		if e <= 0 || e >= len(arr) {
			continue
		}
		arr[e-1], arr[i] = arr[i], arr[e-1]
	}

	for i := range arr {
		if arr[i] != i+1 {
			return i + 1
		}
	}

	return len(arr) + 1
}
```
