---
title: "Implement bubble sort in Python"
summary: "Daily coding practice: Implement bubble sort in Python"
categories: ["Python", "Algorithms"]
tags: ["bubblesort", "sorting"]
#externalUrl: ""
showSummary: true
date: 2023-08-01
draft: false
---

## 1. What is bubble sort?
![Bubble Sort](https://www.computersciencebytes.com/wp-content/uploads/2016/10/bubble_sort.png)

Bubble sort is an algorithm that sequentially compares adjacent elements in a loop and swaps them if the next element is smaller than the current element. The process continues until no further swaps are required.

- **Worst complexity**: n^2
- **Average complexity**: n^2
- **Best complexity**: n
- **Space complexity**: 1
## 2. Visualize
![Bubble Sort](http://blogs.cuit.columbia.edu/zp2130/files/2018/12/Bubble_Sort.gif)
## 3. Implementation

```python

def bubble_sort(arr):
    while True:
        has_swap = False
        for i in range(len(arr)-1):
            if arr[i] > arr[i+1]:
                temp = arr[i]
                arr[i] = arr[i+1]
                arr[i+1] = temp
                has_swap = True
        if has_swap = False:
            break

    return arr

```
