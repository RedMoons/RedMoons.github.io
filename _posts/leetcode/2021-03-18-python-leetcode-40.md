---
title: "Leetcode Python - 39. Combination Sum"
excerpt: "Leetcode #39"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Combination Sum
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #39 - Combination Sum
리트코드의 문제 39 'Combination Sum'을 파이썬으로 풀어 보도록 하겠습니다. 

이 문제는 int의 list를 받아 합이 target이 되는 중복 가능한 조합을 구하는 문제입니다.
discuss의 한 답안을 보도록 하겠습니다.

dfs(깊이 우선 탐색 / Depth First Search)를 이용해 풀 수 있습니다.
```combinationSum``` 함수 자체는 심플하게 짜줍니다.
```python
def combinationSum(self, candidates, target):
    res = []
    self.getCombination(candidates, target, [], res)
    return res
```

그러고 나서 ```getCombination``` 함수를 구현하는데,
```r```값으로 합이 ```target```이 되는 list를 담고 나서,
```res```에 결과 값을 담아줍니다.
```python
def getCombination(self, cs, target, r, res):
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
```cs```는 중복되는 결과를 방지 위해 ```cs[c:]```
```target```은 해당 값을 제외해서 ```target-cs[c]```
```r```은 기존에서 더해진 값을 합해 ```r+[cs[c]]```

```python
for c in range(len(cs)):
    self.getCombination(cs[c:], target - cs[c], r + [cs[c]], res)
```

전체 코드는 아래와 같습니다.
```python
class Solution:
    def combinationSum(self, candidates, target):
        res = []
        self.getCombination(candidates, target, [], res)
        return res
    
    def getCombination(self, cs, target, r, res):
        if target == 0:
            res.append(r)
            return
        if target < 0:
            return
        for c in range(len(cs)):
            self.getCombination(cs[c:], target - cs[c], r + [cs[c]], res)
```

시간복잡도는 최악의 경우 O(30**30) : ```1 <= candidates.length <= 30```

공간복잡도는 O(N) : 상수 target, list r과 res를 저장
