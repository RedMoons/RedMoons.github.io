---
title: "Leetcode Python - 48. Rotate Image"
excerpt: "Leetcode #48"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Rotate Image
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #48 - Rotate Image
리트코드의 문제 48 'Rotate Image'을 파이썬으로 풀어 보도록 하겠습니다. 

이 문제는 2중 list를 받아서, 시계방향으로 90도 회전시키는 문제입니다.

문제 조건으로 새로운 2중 list을 만들지 않아야 하므로,
저는 2중 list에 결과를 append하고, 기존 것을 pop해서 풀었습니다.

먼저 90도 회전한 결과값을 추가해줍니다.
```python
for row in zip(*matrix):
    t = []
    t += [row[len(matrix[0])-k-1] for k in range(len(matrix[0]))]
    matrix.append(t)
```

그러고 기존의 값들을 빼줍니다.
```python
for _ in range(len(matrix[0])):
    matrix.pop(0) 
```

전체 코드는 아래와 같습니다.
```python
class Solution:
    def rotate(self, matrix):
        for row in zip(*matrix):
            t = []
            t += [row[len(matrix[0])-k-1] for k in range(len(matrix[0]))]
            matrix.append(t)
        
        for _ in range(len(matrix[0])):
            matrix.pop(0) 
```

시간복잡도는 O(n²) : loop를 n번 돌면서, 다시 n번 돈다.
```matrix.length == n```
```matrix[i].length == n```
```1 <= n <= 20```

공간복잡도는 O(n²) : n²에 두배가 되므로 2n²