---
title: "Leetcode Python - 55. Jump Game"
excerpt: "Leetcode #55"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Jump Game
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #55 - Jump Game
리트코드의 문제 55 'Jump Game'을 파이썬으로 풀어 보도록 하겠습니다. 

이 문제는 주어진 list에서 각 주어진 element만큼 index로 점프를 할 수 있는데, 
이 값이 list의 마지막에 도달 할 수 있으면 True, 도달 할 수 없으면 False를 반환하는 문제입니다.

discuss의 답안을 보도록 하겠습니다.
정말 심플하게 풀었습니다.. 대단하십니다..

먼저 최대 도달할 수 있는 값 m을 선언 합니다.
그러고 만약에 m이 index보다 작으면 도달할 수 없다는 것이므로 False를 리턴해 줍니다.
그리고 m은 index+value 의 합과 비교해 max로 구해줍니다.

전체 코드는 아래와 같습니다.
```python
class Solution:
    def canJump(self, nums):
        m = 0
        for i,n in enumerate(nums):
            if i > m:
                return False
            m = max(m, i+n)
        return True
```

시간복잡도는 O(n) : 한 번의 loop만 있으므로

공간복잡도도 O(3n)이므로 O(n)이 됩니다. (m,i,n 선언)