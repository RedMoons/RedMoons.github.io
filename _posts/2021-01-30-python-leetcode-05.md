---
title: "Leetcode Python - Longest Palindromic Substring"
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
---

## Leetcode #5 - Longest Palindromic Substring
리트코드의 5번 문제 'Longest Palindromic Substring'을 파이썬으로 풀어 보도록 하겠습니다. 
이 문제는 string에서 앞뒤로 순서가 같은 가장 긴 단어를 반환하는 문제입니다.
[https://leetcode.com/problems/longest-palindromic-substring/](https://leetcode.com/problems/longest-palindromic-substring/)


discuss에 올라온 파이썬 해설을 보도록 합시다.
포인트는 helper 함수를 만들어 현재 위치에서 좌우를 보면서 같으면 더하고 다르면 리턴해 줍니다.
그리고 짝수의 경우와 홀수의 경우를 나누어 그중에 큰 값을 return 해 줍니다.

먼저 helper 함수를 보면 아래와 같습니다.
```python
    def helper(self, s, l, r):
        while l>=0 and r<len(s) and s[l]==s[r]:
            l+=1; r-=1
        return s[l+1:r]
```

짝수의 경우에는 예로, aba이므로 l과 r이 같은 b에서 시작할 수 있지만, 홀수의 경우 abba이므로 bb가 되야하므로 l과 r을 1차이를 둡니다.
그래서 전체 코드는
```python
class Solution:
    def longestPalindrome(self, s: str) -> str:
        
        res = ""
        for i in range(len(s)):
            res = max(self.helper(s,i,i), self.helper(s,i,i+1),res,key=len)
        return res
        
    def helper(self, s, l, r):
        while l>=0 and r<len(s) and s[l]==s[r]:
            l-=1; r+=1
        return s[l+1:r]
```
