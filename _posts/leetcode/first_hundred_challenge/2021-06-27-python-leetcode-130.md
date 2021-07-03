---
title: "Leetcode Python - 130. Surrounded Regions"
excerpt: "Leetcode #130"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Surrounded Regions
  - 알고리즘
  - 파이썬
  - 리트코드
  - dfs
---

## Leetcode #130 - Surrounded Regions
리트코드의 문제 130 'Surrounded Regions'을 파이썬으로 풀어 보도록 하겠습니다. 
주어진 m*n matrix board에 있는 'X','O'를 경계에서 이어져있는 'O'만 남기고 나머지를 'X'로 바꾸는 문제입니다.

예를 들면 아래와 같습니다.
```python
# input
board = [
    ["X","X","X","X"],
    ["X","O","O","X"],
    ["X","X","O","X"],
    ["X","O","X","X"]
 ]

# output
board = [
    ["X","X","X","X"],
    ["X","X","X","X"],
    ["X","X","X","X"],
    ["X","O","X","X"]
]
```

discuss를 보며 풀어 보도록 하겠습니다.

포인트는 boundary 경계쪽에서 시작되는 dfs를 구현하는 것입니다.
그렇기 때문에 'O'가 위에서 시작되는지 아니면 아래에서 시작되는지,
혹은 왼쪽에서 시작되는지 아니면 오른쪽에서 시작되는지 체크해야합니다.

위 혹은 아래에서 시작되는 dfs
```python
for i in [0, len(board)-1]:
    for j in range(len(board[0])):
        self.dfs(board, i, j)  
```

왼쪽 혹은 오른쪽에서 시작되는 dfs
```python
for i in range(len(board)):
    for j in [0, len(board[0])-1]:
        self.dfs(board, i, j)
```

'.'이면 'O'로 나머지는 'X'로, 
```python
for i in range(len(board)):
    for j in range(len(board[0])):
        if board[i][j] == 'O':
            board[i][j] = 'X'
        elif board[i][j] == '.':
            board[i][j] = 'O'
```

dfs 구현, 어느 쪽에서든 이전 것이 'O'이 아니면 진행되지 않음
```python
def dfs(self, board, i, j):
    if 0 <= i < len(board) and 0 <= j < len(board[0]) and board[i][j] == 'O':
        board[i][j] = '.'
        self.dfs(board, i+1, j)
        self.dfs(board, i-1, j)
        self.dfs(board, i, j+1)
        self.dfs(board, i, j-1)
```

전체 코드는 아래와 같습니다.

```python
    def solve(self, board):
        if not board or not board[0]:
            return 
        for i in [0, len(board)-1]:
            for j in range(len(board[0])):
                self.dfs(board, i, j)   
        for i in range(len(board)):
            for j in [0, len(board[0])-1]:
                self.dfs(board, i, j)
        for i in range(len(board)):
            for j in range(len(board[0])):
                if board[i][j] == 'O':
                    board[i][j] = 'X'
                elif board[i][j] == '.':
                    board[i][j] = 'O'
    def dfs(self, board, i, j):
        if 0 <= i < len(board) and 0 <= j < len(board[0]) and board[i][j] == 'O':
            board[i][j] = '.'
            self.dfs(board, i+1, j)
            self.dfs(board, i-1, j)
            self.dfs(board, i, j+1)
            self.dfs(board, i, j-1)
```


시간복잡도는 O(n) : 모든 element를 방문 *2 = 2n

공간복잡도는 O(1) : 상수 안에서 가능
