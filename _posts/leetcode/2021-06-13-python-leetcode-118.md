---
title: "Leetcode Python - 118. Pascal's Triangle"
excerpt: "Leetcode #118"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Pascal's Triangle
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #118 - Pascal's Triangle
리트코드의 문제 118 'Pascal's Triangle'을 파이썬으로 풀어 보도록 하겠습니다. 
Pascal's triangle을 이중 list로 반환하는 문제입니다.

brute force 방식으로 풀었습니다.

```python
class Solution:
    def generate(self, numRows):
        if numRows == 1:
            return [[1]]
        elif numRows == 2:
            return [[1],[1,1]]
        
        res = [[1],[1,1]]
        
        for row in range(2, numRows):
            tmp = []
            for col in range(row+1):
                
                if col == 0:
                    tmp.append(1)
                elif col == row:
                    tmp.append(1)
                else:
                    tmp.append(res[row-1][col-1] + res[row-1][col])
            res.append(tmp)
        return res
```

시간복잡도는 O(n²) : 첫번째 for loop (n) * 두번째 for loop (n-1)


공간복잡도는 O(nᴺ) : res는 nᴺ/2 크기

---

### 개선하기

discuss를 참고해보겠습니다.

```python
resultset = [[1]* (i+1) for i in range(numRows)]
    for i in range(numRows):
        for j in range(1,  i):
            resultset[i][j] = resultset[i-1][j-1] + resultset[i-1][j]

    return resultset
```

위처럼 구현하면 시간복잡도 자체는 그대로이지만, 
라인 수를 많이 줄일수 있습니다.
