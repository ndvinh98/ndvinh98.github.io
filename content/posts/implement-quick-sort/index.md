---
title: "Implement quick sort in Python"
summary: "Daily coding practice: Implement quick sort in Python"
categories: ["Python", "Algorithms"]
tags: ["quicksort", "sorting"]
#externalUrl: ""
showSummary: true
date: 2023-08-06 12:00:00
draft: false
---

## 1. What is quick sort?
![quick Sort](https://www.geeksforgeeks.org/wp-content/uploads/gq/2014/01/QuickSort2.png)

QuickSort is an algorithm that repeatedly partitions the current array around the pivot. The pivot is chosen randomly from the current array. The array is then divided into two sub-arrays, one containing all elements smaller than the pivot element, and the other containing all elements larger than the pivot element. These two arrays are then sorted recursively.

There are many ways to implement it based on the pivot chosen (fist element, random, last element) and partitioning the array (Hoare's partition or Lomuto partition)

- **Worst complexity**: n^2
- **Average complexity**: {{< katex >}}\\( O(n \log n) \\)
- **Best complexity**: n
- **Space complexity**: 1
## 2. Visualize
![quick Sort](http://blogs.cuit.columbia.edu/zp2130/files/2018/12/Quick_Sort.gif)
## 3. Implementation
To understand easily, I used the Lomuto's partition approach and additional memory to implement it

```python

def quick_sort(arr):
    pivot = 0
    if len(arr) <= 1:
        return arr

    left_part = []
    right_part = []
    for i in range(1, len(arr)):
        if arr[i] < arr[pivot]:
            left_part.append(arr[i])
        else:
            right_part.append(arr[i])

    # partition the array around the pivot the call the quick_sort recursively
    left_part = quick_sort(left_part)
    right_part = quick_sort(right_part)

    return left_part + [arr[pivot]] + right_part


if __name__ == "__main__":
    arr = [-4, 99, 2, -9, 5, 2, 1, 10, 3, 12]
    print("Input array: ", arr)
    print("Sorted array: ", quick_sort(arr))


```
