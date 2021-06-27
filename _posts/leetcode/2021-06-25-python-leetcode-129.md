---
title: "Leetcode Python - 129. Sum Root to Leaf Numbers"
excerpt: "Leetcode #129"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Sum Root to Leaf Numbers
  - 알고리즘
  - 파이썬
  - 리트코드
  - dfs
---

## Leetcode #129 - Sum Root to Leaf Numbers
리트코드의 문제 129 'Sum Root to Leaf Numbers'을 파이썬으로 풀어 보도록 하겠습니다. 
주어진 binary tree에서 root에서 마지막 leaf까지의 합들을 더하는문제입니다.

예를 들어 ```root = [1,2,3]```일 때,
결과는 ```'1'+'2'='12'``` + ```'1'+'3'='13'``` = ```'25'``` 가 됩니다.

bruce-force 방식으로 dfs를 이용해 모든 합을 list에 넣어 풀 수 있습니다.

```python
class Solution:
    def sumNumbers(self, root):
        res = []
        self.dfs(root, '', res)
        n = 0
        for i in res:
            n += int(i)
        return n
        
    def dfs(self, root, path, res):
        if root.left is None and root.right is None:
            res.append(path+str(root.val))
            return
        
        if root.left:
            self.dfs(root.left, path+str(root.val), res)
        if root.right:
            self.dfs(root.right, path+str(root.val), res)
```


시간복잡도는 O(n) : 모든 node를 찾아 방문하므로

공간복잡도는 O(n) : res의 크기는 binary tree의 너비만큼, n/2
