---
title: "Leetcode Python - 79. Word Search"
excerpt: "Leetcode #79"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Word Search
  - 알고리즘
  - 파이썬
  - 리트코드
  - dfs
---

## Leetcode #79 - Word Search
리트코드의 문제 79 'Word Search'을 파이썬으로 풀어 보도록 하겠습니다. 

주어진 2중 list에서 특정 단어가 존재하는지 찾는 문제입니다.
discuss를 보도록 하겠습니다.. 

```python
class Solution:
    def exist(self, board, word):
        if not board:
            return False
        for i in range(len(board)):
            for j in range(len(board[0])):
                if self.dfs(board, i, j, word):
                    return True
        return False

    def dfs(self, board, i, j, word):
        if len(word) == 0:
            return True
        if i<0 or i>=len(board) or \
            j<0 or j>=len(board[0]) or \
            word[0]!=board[i][j]:
            return False
        tmp = board[i][j] 
        board[i][j] = "#" 
        
        res = self.dfs(board, i+1, j, word[1:]) or \
                self.dfs(board, i-1, j, word[1:]) or \
                self.dfs(board, i, j+1, word[1:]) or \
                self.dfs(board, i, j-1, word[1:])
        board[i][j] = tmp
        return res
```


시간복잡도는 O(mn) : m * n * 4 * len(word)

공간복잡도는 O(mn) 

