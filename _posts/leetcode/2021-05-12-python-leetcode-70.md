---
title: "Leetcode Python - 70. Climbing Stairs"
excerpt: "Leetcode #70"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Climbing Stairs
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #70 - Climbing Stairs
리트코드의 문제 70 'Climbing Stairs'을 파이썬으로 풀어 보도록 하겠습니다. 

이 문제는 재귀를 이용해 풀 수 있습니다.
```python
class Solution:
    def climbStairs(self, n):
        if n == 1:
            return 1
        if n == 2:
            return 2
        if n == 3:
            return 3
        return self.climbStairs(n-1) + self.climbStairs(n-2)
```

시간복잡도는 O(n) : 도합 2n번 climbStairs 함수가 콜

공간복잡도는 O(n²) : 함수 한 번 불릴 때마다 n이 필요하므로, 2n² 만큼 선언


===
# 개선1

함수 호출을 줄이기 위해서 조금 수정해보았습니다.
```python
    def climbStairs(self, n):
        if n == 1:
            return 1
        if n == 2:
            return 2
        if n == 3:
            return 3
        if n == 4:
            return 5
        if n == 5:
            return 8

        return self.climbStairs(n-4)*5 + self.climbStairs(n-5)*3
```

시간복잡도는 O(n) : 도합 n/2 climbStairs 함수가 콜

공간복잡도는 O(n²) : 함수 한 번 불릴 때마다 n이 필요하므로, n²/2 만큼 선언


# 개선2
discuss를 보도록 하겠습니다.

```python
    def climbStairs(self, n):
        a,b=1,1
        for _ in range(n-1):
            a,b = b, a+b
        return b
```

시간복잡도는 O(n) : loop 한번

공간복잡도는 O(1) : a,b 선언
