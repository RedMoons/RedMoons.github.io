---
title: "Leetcode Python - 221. Maximal Square"
excerpt: "Leetcode #221"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Maximal Square
  - 알고리즘
  - 파이썬
  - 리트코드
  - dynamic programming
---

## Leetcode #221 - Maximal Square

이번에는 특정 챕터별로 문제들을 풀어보겠습니다.
dynamic programming를 집중적으로 풀어보겠습니다.

리트코드의 문제 221 'Maximal Square'을 파이썬으로 풀어 보도록 하겠습니다. 

discuss를 보도록 하겠습니다! ^^ 

포인트는 
1. dp list를 만들 때, 본래 사이즈보다 1씩 큰 사이즈를 만듭니다.
2. 그리고 2*2 list 에서 나머지 3개 값의 min을 구해 값을 구합니다. 거기에 1을 더한 값이 dp에 저장됩니다.


전체 코드는 아래와 같습니다.
```python
class Solution:
    def maximalSquare(self, matrix: List[List[str]]) -> int:
        if matrix is None or len(matrix) < 1:
            return 0
        
        rows = len(matrix)
        cols = len(matrix[0])
        
        dp = [[0]*(cols+1) for _ in range(rows+1)]
        max_side = 0
        
        for r in range(rows):
            for c in range(cols):
                if matrix[r][c] == '1':
                    dp[r+1][c+1] = min(dp[r][c], dp[r+1][c], dp[r][c+1]) + 1 
                    max_side = max(max_side, dp[r+1][c+1])
                
        return max_side * max_side
```

시간복잡도는 O(nm) : matrix 2중 loop

공간복잡도는 O(nm) : matrix 2중 loop가 dp

