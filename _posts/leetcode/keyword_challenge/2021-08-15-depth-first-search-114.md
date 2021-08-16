---
title: "Leetcode Python - 114. Flatten Binary Tree to Linked List"
excerpt: "Leetcode #114"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Flatten Binary Tree to Linked List
  - 알고리즘
  - 파이썬
  - 리트코드
  - depth first search
---

## Leetcode #114 - Flatten Binary Tree to Linked List

이번에는 특정 챕터별로 문제들을 풀어보겠습니다.
depth first search를 집중적으로 풀어보겠습니다.

리트코드의 문제 114 'Flatten Binary Tree to Linked List'을 파이썬으로 풀어 보도록 하겠습니다. 

discuss를 보도록 하겠습니다..

포인트는 prev를 선언해서, 마지막부터 하나씩 root를 더해 나가는 것입니다.

전체 코드는 아래와 같습니다.
```python
class Solution:
    def __init__(self):
        self.prev = None

    def flatten(self, root):
        if not root:
            return None
        self.flatten(root.right)
        self.flatten(root.left)

        root.right = self.prev
        root.left = None
        self.prev = root
```


시간복잡도는 O(n) : n개의 linkedlist를 방문

공간복잡도는 O(1) : 변수 prev 선언



-----
discuss 참고하여 개선

```python
class Solution:
    def maxDepth(self, root):
        if not root:
            return 0

        return 1 + max(self.maxDepth(root.left), self.maxDepth(root.right))
```

시간복잡도는 O(n) : maxDepth 함수를 n번 호출

공간복잡도는 O(1) : 상수
