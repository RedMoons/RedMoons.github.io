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
---

## Leetcode #91 - Decode Ways
리트코드의 문제 91 'Decode Ways'을 파이썬으로 풀어 보도록 하겠습니다. 
알파벳이 encode 되어서 숫자를 가지고 표현될 수 있는 알파벳을 리턴하는 문제입니다.

discuss를 보도록 하겠습니다.
dynamic programming 을 이용해 풀었습니다.

값 0를 가지는 dp list를 만들고, 첫째 값을 1로 해줍니다.
```python
dp = [0 for x in range(len(s)+1)]
dp[0] = 1
```

그 이후 For loop를 돌면서 해당 자릿수가 0이 아니고 1~9일 경우,
혹은 09~27 사이일 경우를 구분해 구해줍니다.

```python
class Solution:
    def numDecodings(self, s):
        if s =="": return 0
        dp [0 for i in range(len(s)+1)]
        dp[0] = 1
        for i in range(1, len(s)+1):
            if s[i-1] != "0":
                dp[i] += dp[i-1]
            if i != 1 and s[i-2:i] < "27" and s[i-2:i] > "09":
                dp[i] += dp[i-2]
          return dp[len(s)]
```

시간복잡도는 O(n) : dynamic programming 을 통해 loop 한번

공간복잡도는 O(n) : dp list
