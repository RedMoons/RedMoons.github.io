---
title: "Leetcode Python - 102. Binary Tree Level Order Traversal"
excerpt: "Leetcode #102"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Binary Tree Level Order Traversal
  - 알고리즘
  - 파이썬
  - 리트코드
  - dfs
---

## Leetcode #102 - Binary Tree Level Order Traversal
리트코드의 문제 102 'Binary Tree Level Order Traversal'을 파이썬으로 풀어 보도록 하겠습니다. 
binary tree root가 주어졌을 때, depth별로 list로 묶어 2중 list를 반환하는 문제입니다.

traverse 함수에 depth 를 파라미터로 넘겨 풀었습니다.
```python
class Solution:
    def levelOrder(self, root):
        ret = []
        if not root:
            return ret
        self.traverse(root, 1, ret)
        return ret
    
    def traverse(self, root, depth, ret):
        if not root:
            return
        if depth > len(ret):
            ret.append([])
        if root:
            ret[depth-1].append(root.val)

        self.traverse(root.left, depth+1, ret)
        self.traverse(root.right, depth+1, ret)
```

시간복잡도는 O(n) : n 갯수만큼 traverse 실행

공간복잡도는 O(n) : root와 같은 크기의 ret
