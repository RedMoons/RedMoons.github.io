---
title: "Leetcode Python - 113. Path Sum II"
excerpt: "Leetcode #113"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Path Sum II
  - 알고리즘
  - 파이썬
  - 리트코드
  - dfs
---

## Leetcode #113 - Path Sum II
리트코드의 문제 113 'Path Sum II'을 파이썬으로 풀어 보도록 하겠습니다. 
binary tree에서 root에서 leaf까지의 합이 targetSum과 같은지 보는 문제입니다.

112문제를 응용해 풀었습니다.

```python
class Solution:
    def pathSum(self, root, targetSum):
        if not root:
            return []
        dp = []
        self.traverse(root, [], dp)
        ret = []
        for i in dp:
            if sum(i) == targetSum:
                ret.append(i)
        return ret
        
    def traverse(self, root, path, dp):
        if not root.left and not root.right:
            dp.append(path+[root.val])
            return 
        if root.left:
            self.traverse(root.left, path + [root.val], dp)
        if root.right:
            self.traverse(root.right, path + [root.val], dp)
```

시간복잡도는 O(n) : n 갯수만큼 traverse 실행 + for 구문 실행 (n)

공간복잡도는 O(n) : 2/n과 같은 크기의 dp생성


