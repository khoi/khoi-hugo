+++
title = "Daily Coding Problem #3 - Serialize binary tree"
date = "2019-02-20T20:47:31+07:00"
draft = false
categories = ["Daily Coding Problem"]
+++

## Problem

This problem was asked by Google.

Given the root to a binary tree, implement serialize(root), which serializes the tree into a string, and deserialize(s), which deserializes the string back into the tree.

For example, given the following Node class

```python
class Node:
    def __init__(self, val, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right
```
The following test should pass:

```python
node = Node('root', Node('left', Node('left.left')), Node('right'))
assert deserialize(serialize(node)).left.left.val == 'left.left'
```

## Solution

One could find a way to serialize a binary tree to a string, but the question doesn't forbid the use of standard lib so I'm going to be lazy and use built in Go's JSON marshaler here and call it a day 😆.

`3_serialize_binary_tree.go`
```go
package daily_coding_problem_in_go

import "encoding/json"

type Node struct {
	Val   string `json:"val"`
	Left  *Node  `json:"left"`
	Right *Node  `json:"right"`
}

func Serialize(n *Node) string {
	b, _ := json.Marshal(n)
	return string(b)
}

func Deserialize(data string) *Node {
	n := new(Node)
	_ = json.Unmarshal([]byte(data), &n)
	return n
}
```

`3_serialize_binary_tree_test.go`
```go
package daily_coding_problem_in_go

import "testing"

func TestDeserialize(t *testing.T) {
	node := &Node{
		Val:   "root",
		Left:  &Node{Val: "left", Left: &Node{Val: "left.left"}},
		Right: &Node{Val: "right"},
	}

	newNode := Deserialize(Serialize(node))

	if newNode.Left.Left.Val != "left.left" {
		t.Errorf("expecting left.left")
	}
}
```

