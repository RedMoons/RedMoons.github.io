---
title: "Leetcode Python - 22. Jump Game II"
excerpt: "Leetcode #22"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Jump Game II
  - 알고리즘
  - 파이썬
  - 리트코드
  - dynamic programming
---

## Leetcode #22 - Jump Game II

이번에는 특정 챕터별로 문제들을 풀어보겠습니다.
dynamic programming를 집중적으로 풀어보겠습니다.

리트코드의 문제 22 'Jump Game II'을 파이썬으로 풀어 보도록 하겠습니다. 

discuss를 보도록 하겠습니다.
포인트는 2개의 포인트를 두어서 하나는 index, 또 하나는 최대로 갈 수 있는 거리로 둡니다.

전체 코드는 아래와 같습니다.
```python
def jump(self, nums):
    if len(nums) <= 1: return 0
    l, r = 0, nums[0]
    time = 1
    while r < len(nums) - 1:
        time += 1
        nxt = max(i + nums[i] for i in range(l, r + 1))
        l, r = r, nxt
    return time
```


시간복잡도는 O(n) : 최악의 경우 e.g [1,1,1,1,1...,1] 

공간복잡도는 O(1) : 상수 l,r,time,nxt 선언

