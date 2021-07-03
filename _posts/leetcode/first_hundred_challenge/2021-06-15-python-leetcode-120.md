---
title: "Leetcode Python - 119. Pascal's Triangle II"
excerpt: "Leetcode #119"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Pascal's Triangle II
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #119 - Pascal's Triangle II
리트코드의 문제 119 'Pascal's Triangle II'을 파이썬으로 풀어 보도록 하겠습니다. 
Pascal's triangle을 rowIndex번째 값을 list로 반환하는 문제입니다.

이전에 풀었던 118번을 응용해서 풀었습니다.

```python
class Solution:
    def getRow(self, rowIndex):
        if not rowIndex:
            return [1]
        
        res = [[1]*(i+1) for i in range(rowIndex+1)]
        
        for i in range(rowIndex+1):
            if i>1:
                for j in range(1, i):
                    res[i][j] = res[i-1][j-1] + res[i-1][j]
        return res[-1]
```

시간복잡도는 O(n²) : 첫번째 for loop (n) * 두번째 for loop (n-1)

공간복잡도는 O(nᴺ) : res는 nᴺ/2 크기
