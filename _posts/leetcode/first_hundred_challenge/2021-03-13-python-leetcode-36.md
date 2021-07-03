---
title: "Leetcode Python - 36. Valid Sudoku"
excerpt: "Leetcode #36"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Valid Sudoku
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #36 - Valid Sudoku
리트코드의 문제 36 'Valid Sudoku'을 파이썬으로 풀어 보도록 하겠습니다. 

이 문제는 Sudoku가 valid한지를 참 거짓을 반환하는 문제입니다.
시간 내로 풀지를 못해서.. discuss의 한 답안을 보도록 하겠습니다.

구현해야 할 조건은 바로 각 row, column, square(3x3)이 1~9까지 중복되지 않고 있는가 입니다.

먼저, 한 unit의 중복체크를 통해 유효를 체크하는 함수입니다.
```python
def is_unit_valid(self, unit):
    unit = [i for i in unit if i != '.']
    return len(set(unit)) == len(unit)
```

다음은 row의 valid 체크하는 함수입니다.
```python
def is_row_valid(self, board):
    for row in board:
        if not self.is_unit_valid(row):
            return False
    return True
```

다음은 column의 valid 체크하는 함수입니다.
```python
def is_col_valid(self, board):
    for col in zip(*board):
        if not self.is_unit_valid(col):
            return False
    return True
```

마지막은 각 square의 valid 체크하는 함수입니다.
```python
def is_square_valid(self, board):
    for i in (0, 3, 6):
        for j in (0, 3, 6):
            square = [board[x][y] for x in range(j, j+3) for y in range(i,i+3)]
            if not self.is_unit_valid(square):
                return False
    return True
```

전체 코드는 아래와 같습니다.
```python
class Solution:
    def isValidSudoku(self, board):
        return (self.is_row_valid(board) and
                self.is_col_valid(board) and
                self.is_square_valid(board))
        
    def is_row_valid(self, board):
        for row in board:
            if not self.is_unit_valid(row):
                return False
        return True

    def is_col_valid(self, board):
        for col in zip(*board):
            if not self.is_unit_valid(col):
                return False
        return True
        
    def is_square_valid(self, board):
        for i in (0,3,6):
            for j in (0,3,6):
                square = [board[x][y] for x in range(j,j+3) for y in range(i,i+3)]
                if not self.is_unit_valid(square):
                    return False
        return True

    def is_unit_valid(self, unit):
        unit = [i for i in unit if i != '.']
        return len(set(unit)) == len(unit)
```

시간복잡도는 O(81)로 상수 안에 끝납니다. (9*9 + 9*9 + 3*3*3*3)

공간복잡도는 O(256)으로 상수 안에 끝납니다.
row : row 9번, i 9*9번
col : col 9번, i 9*9번
square : square 3*3*3*3번, i 3*3*3*3*3번
