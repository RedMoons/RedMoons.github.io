---
title: "Leetcode Python - 5. Longest Palindromic Substring"
excerpt: "Leetcode #5"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Longest Palindromic Substring
  - 알고리즘
  - 파이썬
  - 리트코드
  - dynamic programming
---

## Leetcode #5 - Longest Palindromic Substring

이번에는 특정 챕터별로 문제들을 풀어보겠습니다.
dynamic programming를 집중적으로 풀어보겠습니다.

리트코드의 문제 5 'Longest Palindromic Substring'을 파이썬으로 풀어 보도록 하겠습니다. 

전체 코드는 아래와 같습니다.
```python
class Solution:
    def longestPalindrome(self, s: str) -> str:
        res = ''
        for i in range(len(s)):
            tmp = self.helper(s, i, i)
            res = max(res, tmp, key=len)
            
            tmp = self.helper(s, i, i+1)
            res = max(res, tmp, key=len)
        return res
    
    def helper(self, s, l, r):
        while l >= 0 and r < len(s) and s[l] == s[r]:
            l -= 1
            r += 1
        return s[l+1:r]
```

시간복잡도는 O(n^2) : n/2 (helper) 가 n 번 선언

공간복잡도는 O(1) : tmp,res 선언

