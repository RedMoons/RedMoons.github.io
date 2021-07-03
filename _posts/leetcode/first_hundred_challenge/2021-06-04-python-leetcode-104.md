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
  - dfs
---

## Leetcode #104 - Maximum Depth of Binary Tree
리트코드의 문제 104 'Maximum Depth of Binary Tree'을 파이썬으로 풀어 보도록 하겠습니다. 
주어진 root binary tree에서 maximum depth를 구하는 문제입니다.
이전에 풀었던 traverse 문제를 응용해서 풀 수 있습니다.

```python
class Solution:
    def maxDepth(self, root):
        ret = []
        dep = 1
        if not root:
            return 0
        self.traverse(root, dep, ret)
        return ret[-1]
        
    def traverse(self, root, dep, ret):
        if len(ret) == 0:
            ret.append(dep)
        else:
            ret.append(max(ret[-1],dep))
        if not root:
            return

        if root.left:
            self.traverse(root.left, dep+1, ret)
        if root.right:
            self.traverse(root.right, dep+1, ret)
```


시간복잡도는 O(n) : n 갯수만큼 traverse 실행

공간복잡도는 O(n) : root와 같은 크기의 ret
