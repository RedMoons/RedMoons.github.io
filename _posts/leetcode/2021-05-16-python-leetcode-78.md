---
title: "Leetcode Python - 78. Subsets"
excerpt: "Leetcode #78"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Subsets
  - 알고리즘
  - 파이썬
  - 리트코드
  - dfs
---

## Leetcode #78 - Subsets
리트코드의 문제 78 'Subsets'을 파이썬으로 풀어 보도록 하겠습니다. 

이 문제는 가능한 list의 조합을 구하는 문제입니다. 
이전 문제(77)와 마찬가지로 dfs를 이용해 풀 수 있습니다.
```python
class Solution:
    def subsets(self, nums):
        ret = []
        self.dfs(nums, [], ret)
        return ret
    
    def dfs(self, nums, path, ret):
        ret.append(path)
        if len(nums) == 0:
            return
        for i in range(len(nums)):
            self.dfs(nums[i+1:],path + [nums[i]], ret)
```


시간복잡도는 O(n²) : dfs함수는 (n+(n-1)+(n-2)...+1) 번 호출됨

공간복잡도는 O(n²) : 함수 호출되는 만큼의 공간 차지

