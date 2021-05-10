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
---

## Leetcode #63 - Unique Paths II
리트코드의 문제 63 'Unique Paths II'을 파이썬으로 풀어 보도록 하겠습니다. 

이 문제는 Unique Paths의 응용버전으로 장애물이 있는 문제입니다.
discuss를 보도록 하겠습니다..

2중 list의 맨 앞 row와 high을 구현해준 다음에, Unique Paths를 이용해 풀었습니다.
```python
m = len(obstacleGrid)
n = len(obstacleGrid[0])

obstacleGrid[0][0] = 1 - obstacleGrid[0][0]

for i in range(1, n):
    obstacleGrid[0][i] = 0 if obstacleGrid[0][i] else obstacleGrid[0][i-1]

for i in range(1, m):
    obstacleGrid[i][0] = 0 if obstacleGrid[i][0] else obstacleGrid[i-1][0]
```
값이 1로 장애물이 있다면 0을 구현하고, 값이 0으로 장애물이 없다면 이전 루트 값을 받아옵니다.

이 아래로는 Unique Paths와 같이 구현해주면 됩니다.
```python
for i in range(1, m):
    for j in range(1, n):
        obstacleGrid[i][j] = 0 if obstacleGrid[i][j] else obstacleGrid[i][j-1]+obstacleGrid[i-1][j]
return obstacleGrid[-1][-1]
```


전체는 아래와 같습니다.
```python
class Solution:
    def uniquePathsWithObstacles(self, obstacleGrid):

        m = len(obstacleGrid)
        n = len(obstacleGrid[0])
        obstacleGrid[0][0] = 1 - obstacleGrid[0][0]
        
        for i in range(1, n):
            obstacleGrid[0][i] = 0 if obstacleGrid[0][i] else obstacleGrid[0][i-1]

        for i in range(1, m):
            obstacleGrid[i][0] = 0 if obstacleGrid[i][0] else obstacleGrid[i-1][0]

        for i in range(1, m):
            for j in range(1, n):
                obstacleGrid[i][j] = 0 if obstacleGrid[i][j] else obstacleGrid[i][j-1]+obstacleGrid[i-1][j]
                    
        return obstacleGrid[-1][-1]
```


시간복잡도는 O(m*n) : 2중 loop

공간복잡도는 O(1) : 상수 m,n 선언
