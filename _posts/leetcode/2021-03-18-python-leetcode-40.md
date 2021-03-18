---
title: "Leetcode Python - 40. Combination Sum II"
excerpt: "Leetcode #40"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Combination Sum II
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #40 - Combination Sum II
리트코드의 문제 40 'Combination Sum II'을 파이썬으로 풀어 보도록 하겠습니다. 

이 문제는 int의 list를 받아 합이 target이 되는 중복 허용안하는 조합을 구하는 문제입니다.
이전에 풀었던 #39를 응용해서 풀 수 있습니다.

dfs(깊이 우선 탐색 / Depth First Search)를 이용해 풀 수 있습니다.

```python
def combinationSum2(self, candidates, target):
    res = []
    self.dfs(candidates, target, [], res)
    return res
```

그러고 나서 ```dfs``` 함수를 구현하는데,
```r```값으로 합이 ```target```이 되는 list를 담고 나서,
```res```에 결과 값을 담아줍니다.
```python
def dfs(self, nums, target, r, res):
    if target == 0:
        res.append(r)
        return
```

그리고 ```target```값이 0보다 작으면 더 이상 구하려는 값이 없으므로 return 해줍니다.
```python
if target < 0:
    return
```

마지막으로, dfs를 구현해줍니다.
```nums```는 중복되는 결과를 방지 위해 ```nums[i+1:]```
```target```은 해당 값을 제외해서 ```target-nums[i]```
```r```은 기존에서 더해진 값을 합해 ```r+[nums[i]]```

```python
for i in range(len(nums)):
    if i == 0 or nums[i-1] != nums[i]:
        self.dfs(nums[i+1:], target-nums[i], r+[nums[i]], res)
```

전체 코드는 아래와 같습니다.
```python
class Solution:
    def combinationSum2(self, candidates, target):
        res = []
        candidates.sort()
        self.dfs(candidates, target, [], res)
        return res
    
    def dfs(self, nums, target, r, res):
        if target == 0:
            res.append(r)
            return
        if target < 0:
            return
        for i in range(len(nums)):
            if i == 0 or nums[i-1] != nums[i]:
                self.dfs(nums[i+1:], target-nums[i], r+[nums[i]], res)
```

시간복잡도는 최악의 경우 O(30**30) : 
```1 <= candidates.length <= 100``` 이지만 
```1 <= target <= 30``` 이고, 
```1 <= candidates[i] <= 50``` 이므로, 최대 30번 loop 하면 target이 0보다 작아짐

공간복잡도는 O(N) : 상수 target, list r과 res를 저장
