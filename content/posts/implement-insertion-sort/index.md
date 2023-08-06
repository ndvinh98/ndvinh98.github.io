---
title: "Implement insertion sort in Python"
summary: "Daily coding practice: Implement insertion sort in Python"
categories: ["Python", "Algorithms"]
tags: ["insertionsort", "sorting"]
#externalUrl: ""
showSummary: true
date: 2023-08-02
draft: false
---

## 1. What is insertion sort?
![Insertion Sort](https://he-s3.s3.amazonaws.com/media/uploads/46bfac9.png)


Insertion sort is an algorithm that sequentially moves the current element to the suitable position in the looped part, then updates position of remaining elements in the looped array. The process continues until the loop is end.

- **Worst complexity**: n^2
- **Average complexity**: n^2
- **Best complexity**: n
- **Space complexity**: 1
## 2. Visualize
![Insertion Sort](http://blogs.cuit.columbia.edu/zp2130/files/2018/12/Insertion_Sort.gif)
## 3. Implementation

```python

def insertion_sort(arr):
    def sift_arr(arr, start, end):
        """Function sift elements's index in arr by 1 from end -> start"""
        while start > end:
            arr[start] = arr[start -1]
            start -= 1

    len_arr = len(arr)
    for i in range(len_arr-1):

        # pick insertion element next to current element
        insertion_index = i + 1
        insertion_val = arr[insertion_index]

        for j in range(i, -1, -1):
            # reverse loop from current index till 0
            if insertion_val >= arr[j] and insertion_index-1 == j:
                # next element is >= current element -> Move to next elem
                break

            if insertion_val >= arr[j]:
                # if insert value is >= current reverse array element, insert insertion_val to next to current reverse array element
                arr[j+1] = insertion_val

                # now sift elements index from right side to i by 1
                sift_arr(arr, i+1, j+1)
                break
            else:
                if j != 0:
                    # continue to find correct position
                    continue

                # the picked insertion element is minimum in array. Insert to the first position of the array
                sift_arr(arr, i+1, 0)
                arr[0] = insertion_val

    return arr

```
