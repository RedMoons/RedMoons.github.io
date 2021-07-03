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
  - traverse
---

## Leetcode #94 - Binary Tree Inorder Traversal
리트코드의 문제 94 'Binary Tree Inorder Traversal'을 파이썬으로 풀어 보도록 하겠습니다. 
binary tree가 주어졌을 때, inorder traversal을 순회한 list를 반환하는 문제입니다.

중위 순회를 구현하면 됩니다.
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
시간복잡도는 O(2ⁿ) : 토탈 n만큼 주어졌을 때, 각각 2번 traverse를 실행시킴

공간복잡도는 O(n) : n 길이와 같은 ret선언
