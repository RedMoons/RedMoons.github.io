---
title: "Leetcode Python - 91. Decode Ways"
excerpt: "Leetcode #91"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Decode Ways
  - 알고리즘
  - 파이썬
  - 리트코드
  - dynamic programming
---

## Leetcode #91 - Decode Ways

이번에는 특정 챕터별로 문제들을 풀어보겠습니다.
dynamic programming를 집중적으로 풀어보겠습니다.

리트코드의 문제 91 'Decode Ways'을 파이썬으로 풀어 보도록 하겠습니다. 
discuss를 보도록 하겠습니다.

포인트는 n 번째의 결과값은 n-2과 n-1번째 값으로 표현할 수 있다는 것입니다.


전체 코드는 아래와 같습니다.
```python
class Solution:
    def numDecodings(self, s):
        if not s:
            return 0
        dp = [0 for _ in range(len(s)+1)]
        dp[0] = 1
        dp[1] = 1 if s[0] != '0' else 0
        for i in range(2, len(s)+1):
            if 0 < int(s[i-1:i]) <= 9:
                dp[i] += dp[i-1]
            if 10<= int(s[i-2:i]) <= 26:
                dp[i] += dp[i-2]
        
        return dp[len(s)]
```


시간복잡도는 O(n) : for loop n

공간복잡도는 O(n) : n 사이즈의 list 생성
