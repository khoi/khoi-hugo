+++
title = "Daily Coding Problem #1 - Two Sum"
date = "2019-02-17T12:34:18+07:00"
draft = false
categories = ["Daily Coding Problem"]
+++

From today I'll try to solve a programming problem everyday using Golang and push it to https://github.com/khoi/daily-coding-problem-in-go/
These programing problems are tailored, curated by [Daily Coding Problem](https://www.dailycodingproblem.com/). I highly recommend that you subscribe to them to exercise your brain everyday.

The first problem I'm solving today is `Two Sum`, which is a trivial one.

## Problem

This problem was recently asked by Google.
Given a list of numbers and a number k, return whether any two numbers from the
list add up to k.
For example, given [10, 15, 3, 7] and k of 17, return true since 10 + 7 is 17.
Bonus: Can you do this in one pass?

## Solution

This can be solved in just 1 pass, by storing all the number that we've passed through in a `map[int]struct{}`. And for each element, we check whether the `map[k - currentNumber]` exist. If it exists, we find a match!

**1_two_sum.go**
```go
package daily_coding_problem_in_go

func TwoSum(nums []int, k int) bool {
	m := make(map[int]struct{})

	for _, e := range nums {
		if _, ok := m[k-e]; ok {
			return true
		}
		m[e] = struct{}{}
	}

	return false
}
```

**1_two_sum_test.go**
```go
package daily_coding_problem_in_go

import "testing"

var tests = []struct {
	arr      []int
	k        int
	expected bool
}{
	{[]int{10, 15, 3, 7}, 17, true},
	{[]int{10, 15, 3, 7}, 10, true},
	{[]int{10, 15, 3, 7}, 3, false},
	{[]int{10, 15, 3, 7}, 26, false},
}

func TestTwoSum(t *testing.T) {
	for _, tc := range tests {
		if actual := TwoSum(tc.arr, tc.k); actual != tc.expected {
			t.Errorf("arr = %v, k = %v, got %v, want %v", tc.arr, tc.k, actual, tc.expected)
		}
	}
}
```

Time Complexity: **O(n)**


