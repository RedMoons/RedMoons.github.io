---
title: "Leetcode Python - 101. Symmetric Tree"
excerpt: "Leetcode #101"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Symmetric Tree
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #101 - Symmetric Tree
리트코드의 문제 101 'Symmetric Tree'을 파이썬으로 풀어 보도록 하겠습니다. 
binary tree root가 주어졌을 때, root를 기준으로 좌우대칭이 되는지 보는 문제입니다.

discuss를 보도록 하겠습니다.
root가 None일 때 예외 케이스해주고, isMirror함수를 실행합니다.
```python
def isSymmetric(self, root):
    if root is None:
        return True
    else:
        return self.isMirror(root.left, root.right)
```

left와 right에서 None인 경우들에 True, False를 반환해줍니다.
그 후, val가 같은 경우 iterative하게 풀어줍니다.
```python
def isMirror(self, left, right):
    if left is None and right is None:
        return True
    if left is None or right is None:
        return False

    if left.val == right.val:
        outPair = self.isMirror(left.left, right.right)
        inPiar = self.isMirror(left.right, right.left)
        return outPair and inPiar
    else:
        return False
```


시간복잡도는 O(n) : 갯수만큼 isMirror 실행

공간복잡도는 O(log n) : depth가 log n
