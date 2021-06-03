---
title: "Leetcode Python - 96. Unique Binary Search Trees"
excerpt: "Leetcode #96"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Unique Binary Search Trees
  - 알고리즘
  - 파이썬
  - 리트코드
  - dp
---

## Leetcode #96 - Unique Binary Search Trees
리트코드의 문제 96 'Unique Binary Search Trees'을 파이썬으로 풀어 보도록 하겠습니다. 
int n이 주어졌을 때, 1~n을 가지고 있는 uniq 한 binary search trees의 갯수를 반환하는 문제입니다.

discuss를 보도록 하겠습니다.
dynamic programming을 이용해 풀었습니다.
```python
def numTrees(self, n):
    res = [0] * (n+1)
    res[0] = 1
    for i in range(1, n+1):
        for j in range(i):
            res[i] += res[j] * res[i-1-j]
    return res[n]
```

시간복잡도는 O(n) : dp

공간복잡도는 O(n) : n 길이와 같은 res
