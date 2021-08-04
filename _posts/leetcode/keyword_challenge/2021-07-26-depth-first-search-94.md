---
title: "Leetcode Python - 94. Binary Tree Inorder Traversal"
excerpt: "Leetcode #94"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Binary Tree Inorder Traversal
  - 알고리즘
  - 파이썬
  - 리트코드
  - depth first search
---

## Leetcode #94 - Binary Tree Inorder Traversal

이번에는 특정 챕터별로 문제들을 풀어보겠습니다.
depth first search를 집중적으로 풀어보겠습니다.

리트코드의 문제 94 'Binary Tree Inorder Traversal'을 파이썬으로 풀어 보도록 하겠습니다. 


전체 코드는 아래와 같습니다.
```python
class Solution:
    def inorderTraversal(self, root):
        ret = []
        self.traverse(root, ret)
        return ret
    
    def traverse(self, root, ret):
        if not root:
            return
        self.traverse(root.left, ret)
        if root.val:
            ret.append(root.val)
        self.traverse(root.right, ret)
```


시간복잡도는 O(n) : 총 n번의 traverse 함수 호출

공간복잡도는 O(n) : n 사이즈의 list 생성
