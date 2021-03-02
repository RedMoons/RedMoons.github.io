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
---

## Leetcode #22 - Generate Parentheses
리트코드의 22번 문제 'Generate Parentheses'을 파이썬으로 풀어 보도록 하겠습니다. 

discuss를 보면 정말 쉽고 간결하게 짜신분들이 많은데, 그 중 하나를 보도록 하겠습니다.

기본적으로 recursive하게 접근을 하는데, ```generate```함수를 만들어서 p는 임시 저장 변수로, left와 right은 각 왼쪽 오른쪽 괄호의 숫자를, parens는 결과를 담는 변수입니다.
```python
def generate(p, left, right, parens=[]):
```

다음으로는 recursive 조건들인데, 먼저 '('을 더하면서 left를 빼고, 그다음 ')'을 더하면서 right을 빼고, parens에 p를 더해줍니다.

그 결과 코드는 아래와 같습니다.
```python
def generateParenthesis(self, n):
    def generate(p, left, right, parens=[]):
        if left:         generate(p + '(', left-1, right)
        if right > left: generate(p + ')', left, right-1)
        if not right:    parens += p,
        return parens
    return generate('', n, n)
```

시간복잡도는 O(n) : left가 줄어드는데 n, right이 줄어드는데 n번 generate 함수를 부르게 됩니다.
공간복잡도는 O(n) : generate함수가 불릴 때마다 p, left, right, parens이 선언됩니다.