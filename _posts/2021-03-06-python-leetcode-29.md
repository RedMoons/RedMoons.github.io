---
title: "Leetcode Python - 29. Divide Two Integers"
excerpt: "Leetcode #29"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Divide Two Integers
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #29 - Divide Two Integers
리트코드의 29번 문제 'Divide Two Integers'을 파이썬으로 풀어 보도록 하겠습니다. 

int형 숫자 2개를 받아서, 연산자를 안 쓰고 첫 번째 숫자를 두 번째 숫자로 나눈 몫을 구하는 문제입니다.

discuss 의 한 해답을 보도록 하겠습니다.
우선 곱셈, 나누셈 연산자를 쓰면 안되기 때문에, 일일히 덧셈, 뺄셈을 할경우 시간이 오래 걸리는 이슈가 있습니다.
그래서 여기서는 비트 연산자를 이용하였습니다.

먼저 overflow 케이스를 처리해줍니다.
```python
if dividend == -2**31 and divisor == -1:
    return 2**31-1
```

다음, positive 인지 아닌지를 구하고, 절대값으로 바꾸어 줍니다.
```python
positive = (dividend < 0) is (divisor < 0)
dividend, divisor = abs(dividend), abs(divisor)
```

다음, 비트 연산자를 이용해 몫을 구해줍니다.
```python
while dividend >= divisor:
    t,i = divisor, 1
    while dividend >= t:
        dividend -= t
        res += i
        i <<= 1
        t <<= 1
```

코드는 아래와 같습니다.
```python
class Solution:
    def divide(self, dividend: int, divisor: int):
        if dividend == -2**31 and divisor == -1:
            return 2**31-1
        positive = (dividend > 0 and divisor > 0) or (dividend < 0 and divisor < 0)
        dividend, divisor = abs(dividend), abs(divisor)

        res = 0
        while dividend >= divisor:
            t,i = divisor, 1
            while dividend >= t:
                dividend -= t
                res += i
                i <<= 1
                t <<= 1

        if not positive:
            res = -res
        return res
```

시간 복잡도는 O(n) : 결국 상수를 상수로 나누어 나가는 과정
공간 복잡도는 O(n) : 변수 t,i,res 가 선언되었음
