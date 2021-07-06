---
title: "Leetcode Python - 198. House Robber"
excerpt: "Leetcode #198"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - House Robber
  - 알고리즘
  - 파이썬
  - 리트코드
  - dynamic programming
---

## Leetcode #198 - House Robber

이번에는 특정 챕터별로 문제들을 풀어보겠습니다.
dynamic programming를 집중적으로 풀어보겠습니다.

리트코드의 문제 198 'House Robber'을 파이썬으로 풀어 보도록 하겠습니다. 
이 문제는 주어진 List에서 연속되지 않은 index들의 최대 합을 구하는 문제입니다.

discuss를 보도록 하겠습니다! ^^ 

포인트는 k번째의 최대값은 f(k-2) + nums[k] 혹은 f(k-1) 중에 최대값 인 것입니다.
```python
f(k) = max( f(k-2) + nums[k], f(k-1) )
```

```python
class Solution:
    def rob(self, nums):
        prev = curr = 0
        for num in nums:
            temp = prev
            prev = curr
            curr = max(num + temp, prev)
        return curr
```


시간복잡도는 O(n) : nums loop

공간복잡도는 O(1) : 변수 prev, curr, temp 선언

