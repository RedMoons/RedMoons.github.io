---
title: "Leetcode Python - 128. Longest Consecutive Sequence"
excerpt: "Leetcode #128"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Longest Consecutive Sequence
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #128 - Longest Consecutive Sequence
리트코드의 문제 128 'Longest Consecutive Sequence'을 파이썬으로 풀어 보도록 하겠습니다. 
주어진 list에서 순서 상관없이 연속된 숫자가 몇개나 반복되는지를 return하는 문제입니다.

discuss를 보도록 하겠습니다.
O(n) 시간복잡도를 만족해야 하므로,
list를 set으로 바꾸어줍니다. 그러먼 찾는데 O(1) 시간복잡도로 찾을 수 있습니다.


```python
class Solution:
    def longestConsecutive(self, nums):
        nums = set(nums)
        best = 0
        for x in nums:
            if x - 1 not in nums:
                y = x + 1
                while y in nums:
                    y += 1
                best = max(best, y - x)
        return best
```


시간복잡도는 O(n) : 첫번째 for loop (n) + while loop (1)

공간복잡도는 O(1) : 상수 x,y,best 선언
