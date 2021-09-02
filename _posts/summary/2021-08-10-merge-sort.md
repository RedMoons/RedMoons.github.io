---
title: "Merge sort"
excerpt: "머지 소트 정리"

categories:
  - Summary
tags:
  - summary
  - 정리
  - merge sort
  - 정렬
---

## merge sort (병합 정렬)
오늘은 merge sort 시간복잡도 및 구현에 대해 포스팅해 보겠습니다.

#### merge sort 란?


1. merge sort 란?
    * 비교 기반 알고리즘으로 <b>최선 & 최악 시간복잡도가 </b> ```n log n``` 의 안정적인 퍼포먼스를 보여주는 정렬입니다.
    * 분할 정복 방법을 통해 구현됩니다. 주어진 리스트를 잘게 쪼겐 후 합병하는 방식으로 진행됩니다.

2. 샘플 코드

```python
def mergeSort(myList):
    if len(myList) > 1:
        mid = len(myList) // 2
        left, right = myList[:mid], myList[mid:]

        mergeSort(left)
        mergeSort(right)

        i,j = 0, 0
        k = 0

        while i < len(left) and j < len(right):
            if left[i] <= right[j]:
              myList[k] = left[i]
              i += 1
            else:
                myList[k] = right[j]
                j += 1
            k += 1

        while i < len(left):
            myList[k] = left[i]
            i += 1
            k += 1

        while j < len(right):
            myList[k]=right[j]
            j += 1
            k += 1
```


