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

### 3.1 Hoare's partition

```python
def partition(array, start, pivot):
    """This function partitions the array so that the left side is smaller than the pivot and the right side is larger than the pivot."""

    # make a flag to check whether the pivot is swapped or not
    has_pivot_swapped = False

    # loop through all elements until the left is smaller than the pivot and the right is larger than the pivot
    while not has_pivot_swapped:
        #
        swapable_index = None
        is_swapped = False

        # loop from start index to the pivot index
        for i in range(start, pivot):
            if array[i] >= array[pivot]:
                # If the current element is larger than the pivot, check and set `swapable_index` to the current index if it hasn't been assigned a value.
                if swapable_index is None:
                    swapable_index = i
            else:
                if swapable_index is None:
                    # if the swapable_index is not set, skip it
                    continue
                else:
                    # swap the current element with the element at the swappable_index
                    array[i], array[swapable_index] = array[swapable_index], array[i]
                    # reset swapable_index index to re check again
                    swapable_index = None

                    # mark as is_swapped to continue the loop to partition
                    is_swapped = True
                    break

        if swapable_index is not None and not is_swapped:
            # if the swapable_index is set and the other element is larger than the pivot, Swap the element with the pivot
            array[swapable_index], array[pivot] = array[pivot], array[swapable_index]
            return swapable_index

        if not swapable_index and not is_swapped:
            # the pivot is the last element
            return pivot


def quick_sort(array, start=None, end=None):
    if start is None:
        start = 0
    if end is None:
        end = len(array) - 1

    if start >= end:
        return array

    pivot = partition(array, start, end)
    # partition left array
    quick_sort(array, start, pivot - 1)

    # partition right array
    quick_sort(array, pivot + 1, end)
    return array


if __name__ == "__main__":
    arr = [-4, 99, 2, -9, 5, 2, 1, 10, 3, 12]
    print("Input array: ", arr)
    print("Sorted array: ", quick_sort(arr))
```

### 3.2 Lomuto's partition + Additional Memory

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
