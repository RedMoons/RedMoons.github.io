---
title: "Leetcode Python - 77. Combinations"
excerpt: "Leetcode #77"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Combinations
  - 알고리즘
  - 파이썬
  - 리트코드
  - dfs
---

## Leetcode #77 - Combinations
리트코드의 문제 77 'Combinations'을 파이썬으로 풀어 보도록 하겠습니다. 

이 문제는 가능한 list의 조합을 구하는 문제입니다.
dfs를 이용해 풀 수 있습니다.
```python
def combine(self, n, k):
    ret = []
    self.dfs(list(range(1, n+1)), k, [], ret)
    return ret
```

dfs 함수를 구현합니다.
```python
def dfs(self, nums, k, path, ret):
    if len(path) == k:
        ret.append(path)
        return 
    for i in range(len(nums)):
        self.dfs(nums[i+1:], k, path+[nums[i]], ret)
```




시간복잡도는 O(n²) : dfs함수는 (n+(n-1)+(n-2)...+1) 번 호출됨

공간복잡도는 O(n²) : 함수 호출되는 만큼의 공간 차지

