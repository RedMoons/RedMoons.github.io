---
title: "Leetcode Python - 63. Unique Paths II"
excerpt: "Leetcode #63"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Unique Paths II
  - 알고리즘
  - 파이썬
  - 리트코드
  - dynamic programming
---

## Leetcode #63 - Unique Paths II

이번에는 특정 챕터별로 문제들을 풀어보겠습니다.
dynamic programming를 집중적으로 풀어보겠습니다.

리트코드의 문제 63 'Unique Paths II'을 파이썬으로 풀어 보도록 하겠습니다. 

m과 n이 주어지면, 마지막까지 도달할 수 있는 유니크 path의 갯수를 return하는 문제입니다.
62번 문제에서 중간에 장애물이 나타날 수 있다는 점이 추가되었습니다.

discuss를 보도록 하겠습니다..

포인트는 ``` * (1 - obstacleGrid)```를 이용하는 것입니다.

전체 코드는 아래와 같습니다.
```python
def uniquePathsWithObstacles(self, obstacleGrid):
    if not obstacleGrid:
        return 
    r, c = len(obstacleGrid), len(obstacleGrid[0])
    dp = [[0 for _ in range(c)] for _ in range(r)]
    dp[0][0] = 1 - obstacleGrid[0][0]
    for i in range(1, r):
        dp[i][0] = dp[i-1][0] * (1 - obstacleGrid[i][0])
    for i in range(1, c):
        dp[0][i] = dp[0][i-1] * (1 - obstacleGrid[0][i])
    for i in range(1, r):
        for j in range(1, c):
            dp[i][j] = (dp[i][j-1] + dp[i-1][j]) * (1 - obstacleGrid[i][j])
    return dp[-1][-1]
```


시간복잡도는 O(mn) : for loop m*n

공간복잡도는 O(mn) : m*n 크기의 이중 배열 생성

