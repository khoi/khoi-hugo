+++
title = "Daily Coding Problem Final"
date = "2019-08-21T18:04:33+07:00"
draft = false
categories = ["Daily Coding Problem"]
+++

Writing a blog post for each daily coding problem is getting tedious 😂. Thus, I'll put all my notes and thoughts on it here. All of my solutions can be found on https://github.com/khoi/daily-coding-problem-in-go

### Day 10 - Job Scheduler

With Go routine, this problem is kinda too ez.

### Day 11 - Auto complete

I built a simple [Trie](https://en.wikipedia.org/wiki/Trie) for it. This could be improved with a prefix tree, where nodes that don't have any siblings and children can be combine to its parent.

### Day 14 - Pi estimation with Monte Carlo

![Pi Estimation](/images/pi_estimation_monte_carlo.JPG)

I failed to "parallelize" the algorithm using Go routine. I might revisit this in the future.

### Day 16 - Order Log with Circular List

Learnt that Go has `container/ring` data structure built in.
