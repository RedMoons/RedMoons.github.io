---
title: "Leetcode Python - 90. Subsets II"
excerpt: "Leetcode #90"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Subsets II
  - 알고리즘
  - 파이썬
  - 리트코드
  - dfs
---

## Leetcode #90 - Subsets II
리트코드의 문제 90 'Subsets II'을 파이썬으로 풀어 보도록 하겠습니다. 
discuss를 보도록 하겠습니다.

dfs를 이용해 풀 수 있습니다.
여기서 순서가 없는 부분집합을 구해야하기 때문에
```[1,2]``` 와 ```[2,1]``` 을 같은 집합으로 취급해야 합니다.
또한, 중복된 숫자가 존재하기 때문에, 중복된 숫자가 들어가는 것을 방지해야 합니다.

```python
class Solution:
    def subsetsWithDup(self, nums):
        ret = []
        self.dfs(sorted(nums), [], ret)
        return ret
    
    def dfs(self, nums, path, ret):
        ret.append(path)
        for i in range(len(nums)):
            if i > 0 and nums[i-1] == nums[i]:
                continue
            self.dfs(nums[i+1:], path + [nums[i]], ret)
```

```python
if i > 0 and nums[i-1] == nums[i]:
```
정렬시킨 nums를 위 조건을 통해 같은 값이 들어가는 것을 방지하였습니다.

시간복잡도는 O(2^n) : n이 커질 수록 2의 n 거듭수 만큼 커지고 있음

공간복잡도는 O(n) : ret,path 선언
