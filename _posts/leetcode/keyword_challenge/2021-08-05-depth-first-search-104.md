---
title: "Leetcode Python - 104. Maximum Depth of Binary Tree"
excerpt: "Leetcode #104"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Maximum Depth of Binary Tree
  - 알고리즘
  - 파이썬
  - 리트코드
  - depth first search
---

## Leetcode #104 - Maximum Depth of Binary Tree

이번에는 특정 챕터별로 문제들을 풀어보겠습니다.
depth first search를 집중적으로 풀어보겠습니다.

리트코드의 문제 104 'Maximum Depth of Binary Tree'을 파이썬으로 풀어 보도록 하겠습니다. 

순회를 이용해 풀 수 있습니다.

전체 코드는 아래와 같습니다.
```python
class Solution:
    def maxDepth(self, root: TreeNode) -> int:
        if not root:
            return 0
        res=[]
        self.traverse(root, 0, res)
        return max(res)
        
    def traverse(self, root, path, res):
        if root is None:
            res.append(path)
            return
        self.traverse(root.left, path+1, res)
        self.traverse(root.right, path+1, res)
```


시간복잡도는 O(n) : traverse 함수를 n 번 호출

공간복잡도는 O(n) : 최악의 경우 n/2 크기의 res 생성



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
