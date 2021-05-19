---
title: "Leetcode Python - 81. Search in Rotated Sorted Array II"
excerpt: "Leetcode #81"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Search in Rotated Sorted Array II
  - 알고리즘
  - 파이썬
  - 리트코드
  - binary search
---

## Leetcode #81 - Search in Rotated Sorted Array II
리트코드의 문제 81 'Search in Rotated Sorted Array II'을 파이썬으로 풀어 보도록 하겠습니다. 

임의의 pivot으로 회전된 (오름정렬되었던) list에서 target이 존재하면 true, 아니면 false 반환하는 문제입니다.



binary search를 이용해 풀 수 있습니다.
```python
class Solution:
    def search(self, nums, target):
        
        low, high = 0, len(nums)-1
        while low <= high:
            mid = (low+high)//2
            while low < mid and nums[low] == nums[mid]:
                low += 1
            while mid < high and nums[high] == nums[mid]:
                high -= 1
            if nums[mid] == target:
                return True
            if nums[low] <= nums[mid]:
                if nums[low] <= target < nums[mid]:
                    high = mid-1
                else:
                    low = mid+1
            else:
                if nums[mid] < target <= nums[high]:
                    low = mid+1
                else:
                    high = mid-1
        return False
```

여기서 눈여겨 볼 것은 중복되는 값들을 제거하기 위해, 아래와 같이 low,high를 더하고 빼줍니다.
```python
while low < mid and nums[low] == nums[mid]:
    low += 1
while mid < high and nums[high] == nums[mid]:
    high -= 1
```

시간복잡도는 O(log n) : binary search

공간복잡도는 O(1) : low,mid,high 선언
