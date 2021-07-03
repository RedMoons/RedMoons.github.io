---
title: "Leetcode Python - 103. Binary Tree Zigzag Level Order Traversal"
excerpt: "Leetcode #103"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Binary Tree Zigzag Level Order Traversal
  - 알고리즘
  - 파이썬
  - 리트코드
  - dfs
---

## Leetcode #103 - Binary Tree Zigzag Level Order Traversal
리트코드의 문제 103 'Binary Tree Zigzag Level Order Traversal'을 파이썬으로 풀어 보도록 하겠습니다. 
102번 문제에 짝수 홀수 depth별로 좌에서 우로, 우에서 좌로 읽은 결과를 반환하는 문제입니다.

102번 문제에 depth 짝수 경우에 reverse를 시켜준다.

```python
class Solution:
    def zigzagLevelOrder(self, root):
        ret = []
        if not root:
            return ret        
        self.traverse(root, 1, ret)

        for i in range(len(ret)):
            if i%2:
                ret[i] = ret[i][::-1] 
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
