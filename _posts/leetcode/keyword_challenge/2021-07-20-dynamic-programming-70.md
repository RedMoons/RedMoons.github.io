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
  - dynamic programming
---

## Leetcode #70 - Climbing Stairs

이번에는 특정 챕터별로 문제들을 풀어보겠습니다.
dynamic programming를 집중적으로 풀어보겠습니다.

리트코드의 문제 70 'Climbing Stairs'을 파이썬으로 풀어 보도록 하겠습니다. 


전체 코드는 아래와 같습니다.
```python
class Solution:
    def climbStairs(self, n):
        if not n:
            return 0
        prev, cur = 0, 1
        while n > 0:
            prev, cur = cur, prev+cur
            n -= 1
        return cur
```


시간복잡도는 O(n) : for loop n

공간복잡도는 O(1) : prev, cur 선언

