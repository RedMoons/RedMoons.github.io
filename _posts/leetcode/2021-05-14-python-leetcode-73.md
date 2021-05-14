---
title: "Leetcode Python - 73. Set Matrix Zeroes"
excerpt: "Leetcode #73"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Set Matrix Zeroes
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #73 - Set Matrix Zeroes
리트코드의 문제 73 'Set Matrix Zeroes'을 파이썬으로 풀어 보도록 하겠습니다. 

이 문제는 2중 list가 주어지면, 값으로 0이 있다면 행과 열을 전부 0으로 바꿔주는 문제입니다.
예를 들면 아래와 같습니다.

As is
```python
[
    [1,1,1],
    [1,0,1],
    [1,1,1]
]
```
To be
```python
[
    [1,0,1],
    [0,0,0],
    [1,0,1]
]
```

discuss를 보도록 하겠습니다.

1. 첫째 행과 첫째 열에서 0가 있는지 체크
2. 둘째 행 ~ 마지막 행, 둘째 열 ~ 마지막 열에서 0이 있으면 첫째 행과 첫째 열을 0으로 바꿔줍니다.
3. 첫째 행과 첫째 열에 0이 있으면 필요 부분에 0으로 변경해줍니다.
4. 마지막으로, 1)에서 확인했듯이 처음에 0이 있다면 첫째 행과 첫째 열을 0으로 변경해줍니다.


하나씩 구현해보면,
1. 첫째 행과 첫째 열에서 0가 있는지 체크
```python
row_zero = False
if 0 in list(zip(*matrix))[0]:
    row_zero = True   

col_zero = False
if 0 in matrix[0]:
    col_zero = True
```

2. 둘째 행 ~ 마지막 행, 둘째 열 ~ 마지막 열에서 0이 있으면 첫째 행과 첫째 열을 0으로 바꿔줍니다.
```python
for i in range(1, m):
    for j in range(1, n):
        if matrix[i][j] == 0:
            matrix[i][0] = 0
            matrix[0][j] = 0
```

3. 첫째 행과 첫째 열에 0이 있으면 필요 부분에 0으로 변경해줍니다.
```python
for i in range(1, m):
    if matrix[i][0] == 0:
        for j in range(1, n):
            matrix[i][j] = 0

for j in range(1, n):
    if matrix[0][j] == 0:
        for i in range(1, m):
            matrix[i][j] = 0
```

4. 마지막으로, 1)에서 확인했듯이 처음에 0이 있다면 첫째 행과 첫째 열을 0으로 변경해줍니다.
```python
if col_zero:
    for j in range(n):
        matrix[0][j] = 0
if row_zero:
    for i in range(m):
        matrix[i][0] = 0
```

전체 코드는 아래와 같습니다.
```python
class Solution:
    def setZeroes(self, matrix):
    m = len(matrix)
    n = len(matrix[0])
    
    row_zero = False
    if 0 in list(zip(*matrix))[0]:
        row_zero = True   

    col_zero = False
    if 0 in matrix[0]:
        col_zero = True
            
    for i in range(1, m):
        for j in range(1, n):
            if matrix[i][j] == 0:
                matrix[i][0] = 0
                matrix[0][j] = 0
    
    for i in range(1, m):
        if matrix[i][0] == 0:
            for j in range(1, n):
                matrix[i][j] = 0
                
    for j in range(1, n):
        if matrix[0][j] == 0:
            for i in range(1, m):
                matrix[i][j] = 0
    
    if col_zero:
        for j in range(n):
            matrix[0][j] = 0
    if row_zero:
        for i in range(m):
            matrix[i][0] = 0
```


시간복잡도는 O(n²) : 2중 loop

공간복잡도는 O(1) : 상수 m,n,i,j,col_zero,row_zero 선언