---
title: "Implement selection sort in Python"
summary: "Daily coding practice: Implement selection sort in Python"
categories: ["Python", "Algorithms"]
tags: ["selectionsort", "sorting"]
#externalUrl: ""
showSummary: true
date: 2023-08-02
draft: false
---

## 1. What is selection sort?

Selection sort is an algorithm that sequentially finds the minimum element in a loop and swaps it with the current element. The process continues until the loop is end.

- **Worst complexity**: n^2
- **Average complexity**: n^2
- **Best complexity**: n
- **Space complexity**: 1

## 2. Implementation

```python

def selection_sort(arr):
    len_arr = len(arr)
    for i in range(len_arr -1):
        min_ele_index = i

        for j in range(i+1, len_arr):
            if arr[j] < arr[min_ele_index]:
                min_ele_index = j

        if min_ele_index == i:
            continue

        temp = arr[i]
        arr[i] = arr[min_ele_index]
        arr[min_ele_index] = temp
    return arr

```
