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
  - depth first search
---

## Leetcode #101 - Symmetric Tree

이번에는 특정 챕터별로 문제들을 풀어보겠습니다.
depth first search를 집중적으로 풀어보겠습니다.

리트코드의 문제 101 'Symmetric Tree'을 파이썬으로 풀어 보도록 하겠습니다. 

discuss를 보도록 하겠습니다...
포인트는 stack을 이용해 값들을 받으면서 DFS 돌며 풀 수 있습니다.

전체 코드는 아래와 같습니다.
```python
class Solution:
    def isSymmetric(self, root):
        if not root:
            return False
        stack = [(root.left, root.right)]
        while stack:
            left, right = stack.pop()
            
            if left is None and right is None:
                continue
            if left is None or right is None:
                return False
            if left.val == right.val:
                stack.append((left.left, right.right))
                stack.append((left.right, right.left))
            else:
                return False
        return True
```


시간복잡도는 O(log n) : 최악의 경우 2ˣ=n (depth 만큼 수행)

공간복잡도는 O(n) : 최악의 경우 n/2 크기의 stack이 생성됨.
