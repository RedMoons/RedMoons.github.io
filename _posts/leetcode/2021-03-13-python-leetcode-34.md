---
title: "Leetcode Python - 34. Find First and Last Position of Element in Sorted Array"
excerpt: "Leetcode #34"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Find First and Last Position of Element in Sorted Array
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #34 - Find First and Last Position of Element in Sorted Array
리트코드의 문제 34 'Find First and Last Position of Element in Sorted Array'을 파이썬으로 풀어 보도록 하겠습니다. 

이 문제는 오름 정렬된 integer array인 nums을 받아서 target value의 시작과 끝 포지션을 반환하는 문제입니다.

이진탐색을 응용해서 접근할 수 있습니다.
다만 시작 포지션과 끝 포지션을 찾아야 하므로, 이진탐색을 한 번은 시작 포지션을 찾는데, 한 번은 끝 포지션을 찾는데 하도록 하겠습니다.

전체 코드는 아래와 같습니다.
```python
class Solution:
    def searchRange(self, nums, target):
        low, high = 0, len(nums)-1
        
        left, right = self.searchLeft(nums,target), self.searchRight(nums,target)
        res = [left, right]
        return res
    
    def searchLeft(self, nums, target):
        low, high = 0, len(nums)-1
        res = -1
        while low <= high:
            mid = int((low+high)/2)
            if nums[mid] == target:
                res = mid
                high = mid - 1
            elif nums[mid] < target:
                low = mid + 1
            else:
                high = mid - 1
        return res
    
    def searchRight(self, nums, target):
        low, high = 0, len(nums)-1
        res = -1
        while low <= high:
            mid = int((low+high)/2)
            if nums[mid] == target:
                res = mid
                low = mid + 1
            elif nums[mid] < target:
                low = mid + 1
            else:
                high = mid - 1
        return res
```

시간복잡도는 O(log n) : 이진탐색을 독립적으로 두번 실행

공간복잡도는 O(n) : 상수 low, high, mid, res만을 선언함