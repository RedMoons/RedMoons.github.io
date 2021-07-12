---
title: "Leetcode Python - 22. Generate Parentheses"
excerpt: "Leetcode #22"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Generate Parentheses
  - 알고리즘
  - 파이썬
  - 리트코드
  - dynamic programming
---

## Leetcode #22 - Generate Parentheses

이번에는 특정 챕터별로 문제들을 풀어보겠습니다.
dynamic programming를 집중적으로 풀어보겠습니다.

리트코드의 문제 22 'Generate Parentheses'을 파이썬으로 풀어 보도록 하겠습니다. 
f(n-1)에서 각 string index에 ```()```를 넣어가면서 구합니다.

전체 코드는 아래와 같습니다.
```python
class Solution:
    def generateParenthesis(self, n):
        if n == 1:
            return ["()"]
        elif n == 2:
            return ["()()","(())"]
        dp = [["()"], ["()()","(())"]]

        for i in range(3, n+1):
            tmp = []
            for j in dp[-1]:
                for k in range(len(j)):
                    if not j[:k]+"()" + j[k:] in tmp:
                        tmp.append( j[:k]+"()" + j[k:] )
            dp.append(tmp)
        return dp[-1]
```

시간복잡도는 O(n) : n * 2^(n-1) * 2(n-1) = n² * 2ⁿ
    n : 최초 loop
    2^(n-1) : 두번째 loop : n-1번째의 총 개수, 최악의 경우 2의 거듭제곱 (물론 중복 제거해야하지만)
    2(n-1) : 세번째 loop : 각 n-1번째의 값의 길이 (e.g n=2 ```(())```)

공간복잡도는 O(2ⁿ) : 2^0 + 2^1 + ... 2^n = 2^(n+1)-1

