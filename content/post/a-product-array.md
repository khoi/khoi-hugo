+++
title = "Daily Coding Problem #2 - A Product Array"
date = "2019-02-18T20:50:18+07:00"
draft = false
categories = ["Daily Coding Problem"]
+++

## Problem

This problem was asked by Uber.
Given an array of integers, return a new array such that each element at index i
of the new array is the product of all the numbers in the original array except
the one at i.
For example, if our input was [1, 2, 3, 4, 5], the expected output would be
[120, 60, 40, 30, 24]. If our input was [3, 2, 1], the expected output would be
[2, 3, 6].

**Follow-up: what if you can't use division?**

## Thoughts

- Calculate the product of all elements using 1 pass.
- Construct the new array by iterating through the input array again with `new_array[i] = product_in_step1 / array[i]`
- This only work under the assumption that there is no 0 in the array 🤷‍♂️.

## Tests

```go
package daily_coding_problem_in_go

import "testing"

var productArrayTests = []struct {
	in  []int
	out []int
}{
	{[]int{1, 2, 3, 4, 5}, []int{120, 60, 40, 30, 24}},
	{[]int{3, 2, 1}, []int{2, 3, 6}},
}

func TestProductArray(t *testing.T) {
	for _, tc := range productArrayTests {
		if actual := ProductArray(tc.in); !Equal(actual, tc.out) {
			t.Errorf("%v, expected %v, got %v", tc.in, tc.out, actual)
		}
	}
}
```

## Implementation

```go
package daily_coding_problem_in_go

func ProductArray(arr []int) []int {
	product := arr[0]
	result := make([]int, len(arr)) 

	for _, e := range arr[1:] {
		product *= e
	}

	for i, e := range arr {
		result[i] = product / e
	}
	
	return result
}
```

Time Complexity: **O(n)**

## Follow up

Without division, the idea is:

- Input: `arr = [1, 2, 3, 4, 5]`
- Calculate `left = [1, 1*1, 1*1*2, 1*2*3, 1*2*3*4, 1*2*3*4*5]` = `[1, 1, 2, 6, 24]`
- Calculate `right = [5*4*3*2*1, 5*4*3*2, 5*4*3, 5*4, 1]` = `[120, 60, 20, 5, 1]`
- `result = [120, 60, 40, 30, 24]` where `result[i] = left[i] * right[i]`

```go
func ProductArray2(arr []int) []int {
	size := len(arr)
	left := make([]int, size)
	right := make([]int, size)
	result := make([]int, size)

	for i := 0; i < size; i++ {
		left[i] = 1
		right[i] = 1
	}

	for i := 1; i < size; i++ {
		left[i] = arr[i-1] * left[i-1]
	}

	for i := size - 2; i >= 0; i-- {
		right[i] = arr[i+1] * right[i+1]
	}

	for i := 0; i < size; i++ {
		result[i] = left[i] * right[i]
	}

	return result
}
```

Time Complexity: **O(n)** despite the solution looks a tad more complicated.