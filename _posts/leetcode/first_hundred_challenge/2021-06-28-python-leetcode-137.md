---
title: "Leetcode Python - 137. Single Number II"
excerpt: "Leetcode #137"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Single Number II
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #137 - Single Number II
리트코드의 문제 137 'Single Number II'을 파이썬으로 풀어 보도록 하겠습니다. 

136번 문제와 똑같이 풀면 됩니다.


```python
class Solution:
    def singleNumber(self, nums):        
        dic = {n:0 for n in nums}
        
        for n in nums:
            dic[n] += 1
        
        for n in dic.items():
            if n[1] == 1:
                return n[0]
```

시간복잡도는 O(n) : for loop 따로 따로 이므로 O(n)

공간복잡도는 O(n) : n/3+1 크기의 dic 선언

