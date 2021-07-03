---
title: "Leetcode Python - 112. Path Sum"
excerpt: "Leetcode #112"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Path Sum
  - 알고리즘
  - 파이썬
  - 리트코드
  - dfs
---

## Leetcode #112 - Path Sum
리트코드의 문제 112 'Path Sum'을 파이썬으로 풀어 보도록 하겠습니다. 
binary tree에서 root에서 leaf까지의 합이 targetSum과 같은지 보는 문제입니다.

111문제를 응용해 풀었습니다.

```python
class Solution:
    def hasPathSum(self, root, targetSum):
        if not root:
            return False
        res = []
        self.traverse(root, 0, res)
        if targetSum in res:
            return True
        return False
        
    def traverse(self, root, path, res):
        if not root.right and not root.left:
            res.append(path + root.val)
            return
        
        if root.left:
            self.traverse(root.left, path + root.val, res)
        if root.right:
            self.traverse(root.right, path + root.val, res)
```

시간복잡도는 O(n) : n 갯수만큼 traverse 실행 + if in 구문 실행 (n)

공간복잡도는 O(n) : n/2개의 list들을 depth 만큼 생성 res


