---
title: "Leetcode Python - 105. Construct Binary Tree from Preorder and Inorder Traversal"
excerpt: "Leetcode #105"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Construct Binary Tree from Preorder and Inorder Traversal
  - 알고리즘
  - 파이썬
  - 리트코드
  - dfs
---

## Leetcode #105 - Construct Binary Tree from Preorder and Inorder Traversal
리트코드의 문제 105 'Construct Binary Tree from Preorder and Inorder Traversal'을 파이썬으로 풀어 보도록 하겠습니다. 
binary tree 의 preorder 결과와 inorder 결과가 list로 주어졌을 때
실제 binary tree를 구현해 반환하는 문제입니다.

discuss를 보도록 하겠습니다...!

짚어보아야할 포인트는 preorder에 나온 value가 inorder에서의 같은 value의 위치를 기준으로 left와 right을 구분할 수 있다는 것입니다.

```python
def buildTree(self, preorder, inorder):
    if inorder:
        ind = inorder.index(preorder.pop(0))
        root = TreeNode(inorder[ind])
        root.left = self.buildTree(preorder, inorder[0:ind])
        root.right = self.buildTree(preorder, inorder[ind+1:])
        return root
```

시간복잡도는 O(n) : n 갯수만큼 buildTree 실행

공간복잡도는 O(n) : n과 같은 크기의 root
