+++
title = "Sorting Algorithm Visualizations"
date = "2020-01-21T11:08:28+07:00"
draft = false
categories = []
+++

I recently learned about P5 and Processing by watching [The Coding Train](https://www.youtube.com/channel/UCvjgXvBlbQiydffZU7m1_aw). The framework is powerful and simple enough that I was able to build a Sorting Algorithm Visualizations in a weekend:

- https://sort.khoi.io
- https://github.com/khoi/sorting-visualization

I also rendered a much larger version of the website to videos and post it on [Imgur](https://imgur.com/gallery/VQxl1ol), and the post made "The Most Viral Post of the day", which is encouraging.

The visualizations will be moved from Imgur to this post for longevity.

Here is how they are animated: each row contains the same set of values (colors) but shuffled differently. Hence although each row starts differently, at the end of the sort, they should have the same order (sorted).

# Index

- [Insertion Sort](#insertion-sort)
- [Selection Sort](#selection-sort)
- [Quick Sort - Lomuto](#quick-sort---lomuto-partitioning)
- [Quick Sort - Hoare](#quick-sort---hoare-partitioning)
- [Merge Sort](#merge-sort)
- [Bubble Sort](#bubble-sort)
- [Heap Sort](#heap-sort)
- [Shell Sort](#shell-sort)
- [Radix Sort - LSD](#radix-sort---lsd)
- [Comb Sort](#comb-sort)

**Note: It takes a while to load the videos, be patient please.**

## Insertion Sort

{{<video_loop height="100%" width="100%" mp4="/videos/insertion_sort.mp4" autoplay="autoplay">}}

## Selection Sort

Disclaimer: This animation makes Selection sort looks fast. In fact, it's one of the slowest ( complexity O(n^2) )

The reason for it is I can only animate when there is a swap. Although selection sort requires very little swaps, to find the index for swapping is slow (this part is not animated).

{{<video_loop height="100%" width="100%" mp4="/videos/selection_sort.mp4" autoplay="autoplay">}}

## Quick Sort - Lomuto Partitioning

{{<video_loop height="100%" width="100%" mp4="/videos/quick_sort_lomuto.mp4" autoplay="autoplay">}}

## Quick Sort - Hoare Partitioning

{{<video_loop height="100%" width="100%" mp4="/videos/quick_sort_hoare.mp4" autoplay="autoplay">}}

## Merge Sort

{{<video_loop height="100%" width="100%" mp4="/videos/merge_sort.mp4" autoplay="autoplay">}}

## Bubble Sort

{{<video_loop height="100%" width="100%" mp4="/videos/bubble_sort.mp4" autoplay="autoplay">}}

## Heap Sort

{{<video_loop height="100%" width="100%" mp4="/videos/heap_sort.mp4" autoplay="autoplay">}}

## Shell Sort

{{<video_loop height="100%" width="100%" mp4="/videos/shell_sort.mp4" autoplay="autoplay">}}

## Radix Sort - LSD

{{<video_loop height="100%" width="100%" mp4="/videos/radix_sort_lsd.mp4" autoplay="autoplay">}}

## Comb Sort

{{<video_loop height="100%" width="100%" mp4="/videos/comb_sort.mp4" autoplay="autoplay">}}
