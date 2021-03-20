---
title: "Leetcode Python - 46. Permutations"
excerpt: "Leetcode #46"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Permutations
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #46 - Permutations
리트코드의 문제 46 'Permutations'을 파이썬으로 풀어 보도록 하겠습니다. 

이 문제는 int형 list를 받아서 가능한 모든 조합을 return하는 문제입니다.
이 문제도 이전에 풀어보았던 dfs를 이용하여 풀 수 있습니다.

먼저 베이스 함수를 짜줍니다.
```python
def permute(self, nums):
    res = []
    self.dfs(nums, []. res)
    return res
```

그 이후 dfs함수를 구현합니다.
```python
def dfs(self, nums, r, res):
    if not len(nums):
        res.append(r)
        return
    for i in range(len(nums)):
        self.dfs(nums[0:i] + nums[i+1], r + [nums[i]], res)
```

전체 코드는 아래와 같습니다.
```python
class Solution:
    def permute(self, nums):
        res = []
        self.dfs(nums, [], res)
        return res
    
    def dfs(self, nums, r, res):
        if not len(nums):
            res.append(r)
            return
        for i in range(len(nums)):
            self.dfs(nums[0:i]+nums[i+1:], r+[nums[i]], res)
```

시간복잡도는 O(N) : 6!이내로 가능합니다. ```1 <= nums.length <= 6```

공간복잡도는 O(N) : 저장되는 변수가 res, i, r 정도입니다.