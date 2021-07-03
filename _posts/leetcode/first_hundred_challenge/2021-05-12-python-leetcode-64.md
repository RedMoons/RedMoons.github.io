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
---

## Leetcode #64 - Minimum Path Sum
리트코드의 문제 64 'Minimum Path Sum'을 파이썬으로 풀어 보도록 하겠습니다. 

이 문제는 Unique Paths의 응용버전으로 합이 최소가 되는 결과값을 반환하면 됩니다.

1. 이중 리스트의 제일 앞 행과 제일 앞 열을 구해준 후
2. 안 쪽 값들에 대해서는 왼쪽 혹은 위의 값 중 작은 값을 더해주면 됩니다.

```python
m = len(grid)
n = len(grid[0])
        
for i in range(1, n):
    grid[0][i] += grid[0][i-1]
        
for i in range(1, m):
    grid[i][0] += grid[i-1][0]
```
첫번 째 행과 첫번 째 열의 합을 구해 넣어줍니다.

```python
for i in range(1, m):
    for j in range(1, n):
        grid[i][j] += grid[i][j-1] if grid[i-1][j] > grid[i][j-1] else grid[i-1][j]
```
그리고 안에 있는 값을 작은 쪽으로 구해넣어줍니다.

전체코드는 아래와 같습니다.
```python
class Solution:
    def minPathSum(self, grid: List[List[int]]) -> int:
        m = len(grid)
        n = len(grid[0])
        
        for i in range(1, n):
            grid[0][i] += grid[0][i-1]
        
        for i in range(1, m):
            grid[i][0] += grid[i-1][0]
        
        for i in range(1, m):
            for j in range(1, n):
                grid[i][j] += grid[i][j-1] if grid[i-1][j] > grid[i][j-1] else grid[i-1][j]
        
        return grid[-1][-1]
```

시간복잡도는 O(m*n) : 2중 loop

공간복잡도는 O(1) : 상수 m,n 선언
