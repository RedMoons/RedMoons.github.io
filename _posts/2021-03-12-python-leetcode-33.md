---
title: "Leetcode Python - 33. Search in Rotated Sorted Array"
excerpt: "Leetcode #33"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Search in Rotated Sorted Array
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #33 - Search in Rotated Sorted Array
리트코드의 33 문제 'Search in Rotated Sorted Array'을 파이썬으로 풀어 보도록 하겠습니다. 

오름차순 정렬된 list가 있는데, 이 list는 어느 특정 pivot을 기준으로 회전합니다.
예를 들어 nums=[1,2,3,4,5,6,7]이 있는데, pivot index가 3이라면 [4,5,6,7,1,2,3,4]이 됩니다.
이 회전된 list를 받아서 특정 값의 index를 찾는 문제입니다.

이진트리를 이용해 풀어보도록 하겠습니다.
우선, low와 high를 정하고, mid를 구해 target을 구해 나갑니다.
여기서 중요한 것은 어떤 조건에서 low 값을 바꾸어줄지, high 값을 바꾸어줄지 입니다.

총 3가지 경우가 있습니다.
```low < mid < high``` 인 경우
```python
nums=[1,2,3,4,5,6,7]
```
```mid < high < low``` 인 경우
```python
nums=[6,7,1,2,3,4,5]
```
```high < low < mid``` 인 경우
```python
nums=[3,4,5,6,7,1,2]
```

이 경우들을 보면, ```nums[low] <= nums[mid]```인 경우와 아닌 경우로 나눌 수 있습니다.

전체 코드는 아래와 같습니다.
```python
class Solution:
    def search(self, nums, target):
        low, high = 0, len(nums)-1
        
        while low <= high:
            mid = int((low+high)/2)
            
            if nums[mid] == target:
                return mid

            if nums[low] <= nums[mid]:
                if nums[low] <= target <= nums[mid]:
                    high = mid -1
                else:
                    low = mid + 1
            else:
                if nums[mid] <= target <= nums[high]:
                    low = mid + 1
                else:
                    high = mid -1
                
        return -1
```