+++
title = "Daily Coding Problem #6 - Xor Linked List"
date = "2019-02-23T13:47:23+07:00"
draft = true
categories = ["Daily Coding Problem"]
+++

## Problem

This problem was asked by Google.

An XOR linked list is a more memory efficient doubly linked list. Instead of each node holding next and prev fields, it holds a field named both, which is an XOR of the next node and the previous node. Implement an XOR linked list; it has an add(element) which adds the element to the end, and a get(index) which returns the node at index.

If using a language that has no pointers (such as Python), you can assume you have access to get_pointer and dereference_pointer functions that converts between nodes and memory addresses.

## Solution

[6_xor_linked_list.go](https://github.com/khoi/daily-coding-problem-in-go/blob/master/6_xor_linked_list.go)

```go
{{< readfileraw file="/content/daily-coding-problem-in-go/6_xor_linked_list.go" >}}
```

[6_xor_linked_list_test.go](https://github.com/khoi/daily-coding-problem-in-go/blob/master/6_xor_linked_list_test.go)

```go
{{< readfileraw file="/content/daily-coding-problem-in-go/6_xor_linked_list_test.go" >}}
```

