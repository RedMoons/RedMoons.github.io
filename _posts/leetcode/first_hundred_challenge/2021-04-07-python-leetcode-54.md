---
title: "Leetcode Python - 54. Spiral Matrix"
excerpt: "Leetcode #54"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Spiral Matrix
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #54 - Spiral Matrix
리트코드의 문제 54 'Spiral Matrix'을 파이썬으로 풀어 보도록 하겠습니다. 

이 문제는 m x n matrix에서 나선 순서로 모든 matrix의 값을 리턴하는 문제입니다.
discuss의 답안을 보도록 하겠습니다.
pop과 zip을 이용해 풀었습니다.


```python
return matrix and [*matrix.pop(0)] + self.spiralOrder([*zip(*matrix)][::-1])
```

앞의 matrix 는 값이 존재할 때에만 (0이 아닐 때에만) 뒤에 부분을 실행합니다.
다음 [*matrix.pop(0)]은 첫 번째 row를 pop하는데 tuple 형태일 경우 list로 바꾸어줍니다.
여기에 matrix의 나머지 부분을 변환시켜줍니다.

먼저 [*zip(*matrix)] 로 세로로 묶어줍니다.
여기에 [::-1]를 더해 역순으로 정렬합니다.
이러면 ```[[4,5,6],[7,8,9]]```가 ```[(6, 9), (5, 8), (4, 7)]```처럼 정렬됩니다.
이 결과를 가지고 다시 spiralOrder를 실행시켜줍니다.

```python
class Solution:
    def spiralOrder(self, matrix):
        return matrix and [*matrix.pop(0)] + self.spiralOrder([*zip(*matrix)][::-1])
```

시간 복잡도는 O(N) : 최악의 경우 m+n-1 번 실행합니다. m=10,n=10
공간 복잡도는 O(N) 로 실행이 끝납니다.