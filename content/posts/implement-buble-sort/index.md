---
title: "Implement bubblesort in Python"
summary: "Daily coding practice: Implement bubblesort in Python"
categories: ["Python", "Algorithms"]
tags: ["bubblesort", "sorting"]
#externalUrl: ""
showSummary: true
date: 2023-08-01
draft: false
---

## 1. What is bubblesort?
Bubble sort is an algorithm that sequentially compares adjacent elements in a loop and swaps them if the next element is smaller than the current element. The process continues until no further swaps are required.

- **Worst complexity**: n^2
- **Average complexity**: n^2
- **Best complexity**: n
- **Space complexity**: 1


## 2. Implementation
```python

def bubblesort(arr):
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