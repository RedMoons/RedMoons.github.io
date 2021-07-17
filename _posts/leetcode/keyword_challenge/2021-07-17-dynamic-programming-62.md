---
title: "Leetcode Python - 62. Unique Paths"
excerpt: "Leetcode #62"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Unique Paths
  - 알고리즘
  - 파이썬
  - 리트코드
  - dynamic programming
---

## Leetcode #62 - Unique Paths

이번에는 특정 챕터별로 문제들을 풀어보겠습니다.
dynamic programming를 집중적으로 풀어보겠습니다.

리트코드의 문제 62 'Unique Paths'을 파이썬으로 풀어 보도록 하겠습니다. 

m과 n이 주어지면, 마지막까지 도달할 수 있는 유니크 path의 갯수를 return하는 문제입니다.


전체 코드는 아래와 같습니다.
```python
class Solution:
    def uniquePaths(self, m: int, n: int) -> int:
        if m == 1 or n == 1:
            return 1
        matrix = [[1]*n for _ in range(m)]
        for i in range(1, m):
            for j in range(1, n):
                matrix[i][j] = matrix[i-1][j] + matrix[i][j-1]  
        return matrix[m-1][n-1]
```


시간복잡도는 O(mn) : for loop m*n

공간복잡도는 O(mn) : m*n 크기의 이중 배열 생성

