---
title: "Leetcode Python - 43. Multiply Strings"
excerpt: "Leetcode #30"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Multiply Strings
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #43 - Multiply Strings
리트코드의 문제 43 'Multiply Strings'을 파이썬으로 풀어 보도록 하겠습니다. 

이 문제는 string 두 input을 받아서, 곱을 string으로 반환하는 문제입니다.
다만, built-in BigInteger library를 쓰지말 것과 input을 string으로 바로 바꾸지 않는 것이 조건입니다.

먼저, 두 input을 integer로 바꾸어 보겠습니다.
```python
r1 = 0
for i1 in range(len(num1)):
    r1 += int(num1[i1]) * (10**(len(num1)-i1-1))

r2 = 0
for i2 in range(len(num2)):
    r2 += int(num2[i2]) * (10**(len(num2)-i2-1))
```

전체 코드는 아래와 같습니다.
```python
class Solution:
    def multiply(self, num1, num2):
        r1 = 0
        for i1 in range(len(num1)):
            r1 += int(num1[i1]) * (10**(len(num1)-i1-1))
            
        r2 = 0
        for i2 in range(len(num2)):
            r2 += int(num2[i2]) * (10**(len(num2)-i2-1))
            
        return str(r1*r2)
```

시간복잡도는 O(N) : num1과 num2의 길이만큼 loop를 돈다.

공간복잡도는 O(N) : r1,i1,r2,i2만 선언된다.