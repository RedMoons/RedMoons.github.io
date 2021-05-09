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
---

## Leetcode #62 - Unique Paths
리트코드의 문제 62 'Unique Paths'을 파이썬으로 풀어 보도록 하겠습니다. 

이 문제는 linked list를 rotate 시키는 문제입니다.
discuss를 보도록 하겠습니다.. 어서 내공이 쌓여 후딱 후딱 풀 수 있는 그날이 오기를..

핵심은 2차 리스트로 만든 후 왼쪽과 위로부터의 합을 각 element에 올리는 것입니다.

```python
matrix = [[1 for i in range(n)] for i in range(m)]

for i in range(1,m):
    for j in range(1,n):
        matrix[i][j] = matrix[i-1][j] + matrix[i][j-1]
return matrix[-1][-1]
```


시간복잡도는 O(n²) : 2중 loop

공간복잡도는 O(n²) : 2중 list matrix 선언
