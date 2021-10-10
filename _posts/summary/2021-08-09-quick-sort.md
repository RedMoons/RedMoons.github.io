---
title: "Quick sort"
excerpt: "퀵 소트 정리"

categories:
  - Summary
tags:
  - summary
  - 정리
  - quick sort
  - 정렬
---


## Sort 종류별 정리
오늘은 sort 종류별 시간복잡도 및 구현에 대해 포스팅해 보겠습니다.

#### quick sort (퀵 정렬)

1. quick sort 란?
    임의의 pivot을 정하고, 이 값을 기준으로 pivot 왼쪽에는 작은 값을 넣고, 오른쪽에는 큰 값들을 두는 정렬입니다.
    * 위키피디아 : https://ko.wikipedia.org/wiki/%ED%80%B5_%EC%A0%95%EB%A0%AC
    * 평균 시간복잡도 : O(n log n)
    * 최악 시간복잡도 : O(n²)

2. 샘플 코드
파이썬으로 
```python
def quicksort(myList):
    if len(myList) <= 1:
        return myList
    more, less, equal = [], [], []
    pivot = myList[len(myList)//2]
    for i in myList:
        if i < pivot:
            less.append(i)
        elif i > pivot:
            more.append(i)
        else:
            equal.append(i)
    return quicksort(less) + equal + quicksort(more)
```

cache를 안쓰고, 풀 경우
```python
def partition(arr, start, end):
    pivot = arr[start]
    left = start + 1
    right = end
    done = False
    while not done:
        while left <= right and arr[left] <= pivot:
            left += 1
        while left <= right and pivot <= arr[right]:
            right -= 1
        if right < left:
            done = True
        else:
            arr[left], arr[right] = arr[right], arr[left]
    arr[start], arr[right] = arr[right], arr[start]
    return right
```


3. 평균 시간복잡도 & 최악 시간복잡도
    * 위에서도 언급했지만 평균 시간복잡도는 
    (깊이 log n 만큼 수행) * (수행 때 마다 n 번의 비교 필요)로 
    O(n log n) 이 됩니다.
    * 최악의 경우에는 한개의 pivot만 정렬되는경우 
    (n번의 수행) * (n 번 비교 필요)으로
    O(n²) 이 됩니다.

```python
def qsort(arr, low, high):
    if high <= low:
        return
    mid = partition(arr, low, high)
    print('low, mid, high : ',str(low), str(mid), str(high))
    qsort(arr, low, mid - 1)
    qsort(arr, mid, high)
    return arr


def partition(arr, low, high):
    pivot = arr[(low + high) // 2]
    print('pivot : ', str(pivot))
    while low <= high:
        while arr[low] < pivot:
            low += 1
        while arr[high] > pivot:
            high -= 1
        if low <= high:
            arr[low], arr[high] = arr[high], arr[low]
            low, high = low + 1, high - 1
    print('arr : ', arr)
    print('low : ', str(low))
    return low
```
```python
def qsort(arr, low, high):
    if high <= low:
        return
    mid = partition(arr, low, high)
    qsort(arr, low, mid-1)
    qsort(arr, mid, high)
    return arr

def partition(arr, low, high):
    pivot = arr[(low+high)//2]
    while low <= high:
        while arr[low] < pivot:
            low += 1
        while arr[high] > pivot:
            high == 1
        if low <= high:
            arr[low], arr[high] = arr[high], arr[low]
            low += 1
            high -= 1
    return low

```