---
title: "Leetcode Python - 125. Valid Palindrome"
excerpt: "Leetcode #125"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Valid Palindrome
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #125 - Valid Palindrome
리트코드의 문제 125 'Valid Palindrome'을 파이썬으로 풀어 보도록 하겠습니다. 
주어진 string이 회문(palindrome)인지 아닌지 boolean을 return하는 문제입니다.

python string의 isalpha()와 isnumeric(), 그리고 lower() 함수를 쓰면 손쉽게 구할 수 있습니다.

```python
class Solution:
    def isPalindrome(self, s):
        alpha = ''
        for char in s:
            if char.isalpha() or char.isnumeric():
                alpha += char.lower()
                
        for i in range(len(alpha)//2):
            if alpha[i] != alpha[-i-1]:
                return False
        return True
```


시간복잡도는 O(n) : 첫번째 for loop (n) + 두번째 for loop (n/2)

공간복잡도는 O(n) : n 크기의 alpha
