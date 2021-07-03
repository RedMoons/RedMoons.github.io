---
title: "Leetcode Python - 74. Search a 2D Matrix"
excerpt: "Leetcode #74"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Search a 2D Matrix
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #74 - Search a 2D Matrix
리트코드의 문제 74 'Search a 2D Matrix'을 파이썬으로 풀어 보도록 하겠습니다. 

이 문제는 정렬된 2중 list가 주어지면, target 값이 2중 list에 있으면 True, 없으면 False를 반환하는 문제입니다.
예를 들면 아래와 같습니다.

```python
[
    [1 , 3, 5, 7],
    [10,11,16,20],
    [23,30,34,60]
]
, target = 3
```
```return True```

target이 어느 row 사이에 있을지 계산 후 해당 row에 있으면 True를 return 합니다.

전체 코드는 아래와 같습니다.
```python
class Solution:
    def searchMatrix(self, matrix, target):
        m,n = len(matrix), len(matrix[0])
        row = None
        for i in range(m-1):
            if matrix[i][0] <= target and target < matrix[i+1][0]:
                row = i
                break
        if matrix[-1][0] <= target and target <= matrix[-1][-1]:
                row = m-1
        if row != None and target in matrix[row]:
            return True
        
        return False
```


시간복잡도는 O(m+n) : m에 대한 loop와 n에 대한 loop

공간복잡도는 O(1) : 상수 m,n,row 가 선언


### 개선하기
이진탐색을 이용해 시간복잡도를 개선해보겠습니다.
```python
class Solution:
    def searchMatrix(self, matrix, target):
        m,n = len(matrix), len(matrix[0])
        low, high = 0, m*n
        
        while low < high:
            mid = (low+high)//2
            x = matrix[mid//n][mid%n]
            if  x < target:
                low = mid+1
            elif x > target:
                high=mid
            else:
                return True
            
        return False
```

시간복잡도는 O(log(m+n)) : m*n에 대한 이진탐색 트리

공간복잡도는 O(1) : 상수 m,n,row,high,mid,x 가 선언