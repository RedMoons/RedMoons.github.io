---
title: "Leetcode Python - 64. Minimum Path Sum"
excerpt: "Leetcode #64"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Minimum Path Sum
  - 알고리즘
  - 파이썬
  - 리트코드
  - dynamic programming
---

## Leetcode #64 - Minimum Path Sum

이번에는 특정 챕터별로 문제들을 풀어보겠습니다.
dynamic programming를 집중적으로 풀어보겠습니다.

리트코드의 문제 64 'Minimum Path Sum'을 파이썬으로 풀어 보도록 하겠습니다. 

m과 n이 주어지면, 마지막까지 도달할 수 있는 path 중 합의 최소값을 return 하는 문제입니다.

전체 코드는 아래와 같습니다.
```python
class Solution:
    def minPathSum(self, grid):
        if not grid:
            return 0
        m,n = len(grid), len(grid[0])
        for i in range(1, m):
            grid[i][0] = grid[i-1][0] + grid[i][0]
        for i in range(1, n):
            grid[0][i] = grid[0][i-1] + grid[0][i]
        for i in range(1, m):
            for j in range(1, n):
                grid[i][j] = min(grid[i-1][j], grid[i][j-1]) + grid[i][j]
        return grid[-1][-1]
```


시간복잡도는 O(mn) : for loop m*n

공간복잡도는 O(1) : in place 로 grid 이중 배열 안에서 해결

