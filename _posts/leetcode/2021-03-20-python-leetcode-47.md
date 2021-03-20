---
title: "Leetcode Python - 47. Permutations II"
excerpt: "Leetcode #47"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Permutations II
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #47 - Permutations II
리트코드의 문제 47 'Permutations II'을 파이썬으로 풀어 보도록 하겠습니다. 

이 문제는 중복된 int형 list를 받아서 가능한 모든 조합을 return하는 문제입니다.
이전에 풀었던 46번 문제와 유사합니다.
[46 - Permutations](https://redmoons.github.io/python%20algorithm/python-leetcode-46/)

중복된 list를 제거해야하는데, 간단히 제거한 분의 코드를 봐보면
```python
if i > 0 and nums[i-1] == nums[i]:
    continue
```
정렬 후 이 조건으로 모든 중복 list를 추가 안할 수 있습니다.

전체 코드는 아래와 같습니다.
```python
class Solution:
    def permuteUnique(self, nums):
        res = []
        nums.sort()
        self.dfs(nums, [], res)
        return res
    
    def dfs(self, nums, path, res):
        if not nums:
            res.append(path)
            return
        for i in range(len(nums)):
            if i > 0 and nums[i-1] == nums[i]:
                continue
            self.dfs(nums[:i] + nums[i+1:], path + [nums[i]], res)
```

시간복잡도는 O(N!) : 범위 조건 이 있어, 최악의 경우 8!입니다. ```1 <= nums.length <= 8```

공간복잡도는 O(N) : 저장되는 변수가 res, i, path 정도입니다.