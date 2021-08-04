---
title: "Leetcode Python - 100. Same Tree"
excerpt: "Leetcode #100"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Same Tree
  - 알고리즘
  - 파이썬
  - 리트코드
  - depth first search
---

## Leetcode #100 - Same Tree

이번에는 특정 챕터별로 문제들을 풀어보겠습니다.
depth first search를 집중적으로 풀어보겠습니다.

리트코드의 문제 100 'Same Tree'을 파이썬으로 풀어 보도록 하겠습니다. 

discuss를 보도록 하겠습니다...
포인트는 stack을 이용해 값들을 받으면서 DFS 돌며 풀 수 있습니다.

전체 코드는 아래와 같습니다.
```python
class Solution:
def isSameTree(self, p, q):
    stack = [(p, q)]
    while stack:
        node1, node2 = stack.pop()
        if not node1 and not node2:
            continue
        elif None in [node1, node2]:
            return False
        else:
            if node1.val != node2.val:
                return False
            stack.append((node1.right, node2.right))
            stack.append((node1.left, node2.left))
    return True
```


시간복잡도는 O(n) : 최악의 경우 binary tree를 모두 순회해야함.

공간복잡도는 O(n) : 최악의 경우 n/2 크기의 stack이 생성됨.
