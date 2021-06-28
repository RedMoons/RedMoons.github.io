---
title: "Leetcode Python - 136. Single Number"
excerpt: "Leetcode #136"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Single Number
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #136 - Single Number
리트코드의 문제 136 'Single Number'을 파이썬으로 풀어 보도록 하겠습니다. 
int형 list에서 한 element를 제외하고 나머지는 동일한 값이 1개씩 존재하는데, unique 한 값을 반환하는 문제입니다.

dict형을 하나 선언해서 풀었습니다.


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

공간복잡도는 O(n) : n/2+1 크기의 dic 선언

