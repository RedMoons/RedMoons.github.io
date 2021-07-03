---
title: "Leetcode Python - 111. Minimum Depth of Binary Tree"
excerpt: "Leetcode #111"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Minimum Depth of Binary Tree
  - 알고리즘
  - 파이썬
  - 리트코드
  - dfs
---

## Leetcode #111 - Minimum Depth of Binary Tree
리트코드의 문제 111 'Minimum Depth of Binary Tree'을 파이썬으로 풀어 보도록 하겠습니다. 
binary tree에서 minimum depth를 반환하는 문제입니다.

dfs 를 이용해 풀었습니다.

```python
class Solution:
    def minDepth(self, root):
        if not root:
            return 0
        dp = []
        self.traverse(root, 1, dp)
        return min(dp)
        
    def traverse(self, root, depth, dp):
        if not root or (not root.left and not root.right):
            dp.append(depth)
            return
        if root.left:
            self.traverse(root.left, depth+1, dp)
        if root.right:
            self.traverse(root.right, depth+1, dp)
```

시간복잡도는 O(n) : n 갯수만큼 traverse 실행 + min 실행시간 (n)

공간복잡도는 O(n) : n과 같은 크기의 dp생성
