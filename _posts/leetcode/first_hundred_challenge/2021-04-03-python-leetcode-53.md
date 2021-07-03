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
---

## Leetcode #53 - Maximum Subarray
리트코드의 문제 53 'Maximum Subarray'을 파이썬으로 풀어 보도록 하겠습니다. 

이 문제는 list에서 sub array의 합이 최대가 되는 값을 리턴하는 문제입니다.
discuss의 답안을 보도록 하겠습니다.
이 문제는 curSum이랑 maxSum을 선언해서 풀었습니다.

```python
curSum = maxSum = nums[0]
for num in nums[1:]:
    curSum = max(nums, curSum + num)
    maxSum = max(maxSum, curSum)
```

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