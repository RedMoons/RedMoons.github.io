---
title: "Leetcode Python - 53. Maximum Subarray"
excerpt: "Leetcode #53"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Maximum Subarray
  - 알고리즘
  - 파이썬
  - 리트코드
  - dynamic programming
---

## Leetcode #53 - Maximum Subarray

이번에는 특정 챕터별로 문제들을 풀어보겠습니다.
dynamic programming를 집중적으로 풀어보겠습니다.

리트코드의 문제 53 'Maximum Subarray'을 파이썬으로 풀어 보도록 하겠습니다. 

주어진 list에서 연속된 숫자의 합이 가장 큰 값을 반환하는 문제입니다.

discuss를 보도록 하겠습니다.
포인트는 이전까지의 최대합이 그다음 숫자보다 작다면 현재 최대합을 다음 숫자로 하는 것입니다.

예를 들어, ```[2,-1,3]``` 에서 
```2```와 ```2+(-1)```를 비교하면 2가 더 크기 때문에 2가 최대 합이 됩니다.
다음으로 ```2```와 ```3```을 비교하면 3이 더 크기 때문에 3이 최대 합이 됩니다.

전체 코드는 아래와 같습니다.
```python
class Solution:
    def maxSubArray(self, nums):
        if len(nums) == 1:
            return nums[0]

        curSum = maxSum = nums[0]
        for n in nums[1:]:
            curSum =  max(n, n + curSum)
            maxSum = max(maxSum, curSum)
        return maxSum
```


시간복잡도는 O(n) : for loop 한 번

공간복잡도는 O(1) : 상수 curSum, maxSum 선언

