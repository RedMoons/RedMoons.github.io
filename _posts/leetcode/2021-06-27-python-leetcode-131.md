---
title: "Leetcode Python - 131. Palindrome Partitioning"
excerpt: "Leetcode #131"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Palindrome Partitioning
  - 알고리즘
  - 파이썬
  - 리트코드
  - dfs
---

## Leetcode #131 - Palindrome Partitioning
리트코드의 문제 131 'Palindrome Partitioning'을 파이썬으로 풀어 보도록 하겠습니다. 
주어진 string에서 palindrome(회문)이 가능한 partition들로 이루어진 list들의 합을 구하는 문제입니다.

palindrome 함수를 구현하여, dfs를 이용해 풀었습니다.

palindrome 함수
```python
def palindrome(self, s):
    if len(s) == 1:
        return True
    for i in range(len(s)//2):
        if s[i] != s[-i-1]:
            return False
    return True
```

전체 함수는 아래와 같습니다.
```python
class Solution:
    def partition(self, s):
        res = []
        self.dfs(s, [], res)
        return res

    def dfs(self, s, path, res):
        if not s:
            res.append(path)
            return
        for i in range(len(s)):
            if self.palindrome(s[:i+1]):
                self.dfs(s[i+1:], path + [s[:i+1]], res)
        
    def palindrome(self, s):
        if len(s) == 1:
            return True
        for i in range(len(s)//2):
            if s[i] != s[-i-1]:
                return False
        return True
```


시간복잡도는 O(nᴺ) : brute force 방식으로 구현

공간복잡도는 O(2ᴺ) : 최악의 경우, string의 갯수는 2ᴺ
