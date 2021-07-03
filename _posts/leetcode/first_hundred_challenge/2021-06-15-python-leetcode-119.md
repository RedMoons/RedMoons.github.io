---
title: "Leetcode Python - 120. Triangle"
excerpt: "Leetcode #120"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Triangle
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #120 - Triangle
리트코드의 문제 120 'Triangle'을 파이썬으로 풀어 보도록 하겠습니다. 
이중 list Triangle에서 위에서 아래로 합이 최소가 되는 값을 반환하는 문제입니다.

제가 푼 방법으로는 time exceed가 발생해서, discuss를 보도록 하겠습니다.

포인트는 이중 list Triangle과 같은 크기의 res를 구한 뒤,
여기에 합들을 overwrite하는 것입니다.

먼저 초기선언을 해줍니다.
```python
if not triangle:
    return 
res = [[0 for i in range(len(row))] for row in triangle]
res[0][0] = triangle[0][0]
```

그리고 idx 위치에 따라 다르게 구해줍니다. 
양쪽 끝쪽은 합의 계산이 1가지 뿐이지만, 가운데는 위에 중에 작은 쪽을 더해주면 됩니다.
```python
for i in range(1, len(triangle)):
    for j in range(len(triangle[i])):
        if j == 0:
            res[i][j] = res[i-1][j] + triangle[i][j]
        elif j == len(triangle[i])-1:
            res[i][j] = res[i-1][j-1] + triangle[i][j]
        else:
            res[i][j] = min(res[i-1][j-1], res[i-1][j]) + triangle[i][j]
```

전체 코드는 아래와 같습니다.
```python
    def minimumTotal(self, triangle):
        if not triangle:
            return 
        res = [[0 for i in range(len(row))] for row in triangle]
        res[0][0] = triangle[0][0]
        for i in range(1, len(triangle)):
            for j in range(len(triangle[i])):
                if j == 0:
                    res[i][j] = res[i-1][j] + triangle[i][j]
                elif j == len(triangle[i])-1:
                    res[i][j] = res[i-1][j-1] + triangle[i][j]
                else:
                    res[i][j] = min(res[i-1][j-1], res[i-1][j]) + triangle[i][j]
        return min(res[-1])

```


시간복잡도는 O(n²) : 첫번째 for loop (n) * 두번째 for loop (n)

공간복잡도는 O(n²) : res는 n²/2 크기
