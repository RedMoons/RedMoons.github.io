---
title: "Leetcode Python - 139. Word Break"
excerpt: "Leetcode #139"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Word Break
  - 알고리즘
  - 파이썬
  - 리트코드
  - dynamic programming
---

## Leetcode #139 - Word Break

이번에는 특정 챕터별로 문제들을 풀어보겠습니다.
dynamic programming를 집중적으로 풀어보겠습니다.

리트코드의 문제 139 'Word Break'을 파이썬으로 풀어 보도록 하겠습니다. 
이 문제는 주어진 string(s)에서 주어진 wordDic으로 커버가 되는지를 확인하는 것입니다.

discuss를 보도록 하겠습니다! ^^ 

포인트는 dp(dynamic programming)을 응용해 s의 길이와 같은 크기의 list를 만듭니다.
```python
dp = [False for i in range(n+1)]
```

그리고 첫 케이스를 위해서 첫째 index를 True로 해줍니다.
```python
dp[0] = True
```

loop를 돌면서 word들이 있는지 체크하면서 True로 바꾸고, 마지막 값을 반환하면 됩니다.
```python
for i in range(1,n+1):
    for w in wordDict:
        if dp[i-len(w)] and s[i-len(w):i]==w:
            dp[i]=True
```

전체 코드는 아래와 같습니다.
```python
def wordBreak(self, s, wordDict):
    n = len(s)
    dp = [False for i in range(n+1)]
    dp[0] = True
    for i in range(1,n+1):
        for w in wordDict:
            if dp[i-len(w)] and s[i-len(w):i]==w:
                dp[i]=True
    return dp[-1]
```

시간복잡도는 O(nm) : s의 길이를 n, wordDict의 길이를 m이라 하면 mn

공간복잡도는 O(n) : dp의 사이즈 n

