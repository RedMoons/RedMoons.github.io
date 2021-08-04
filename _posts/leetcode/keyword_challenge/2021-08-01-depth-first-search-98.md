---
title: "Leetcode Python - 98. Validate Binary Search Tree"
excerpt: "Leetcode #98"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Validate Binary Search Tree
  - 알고리즘
  - 파이썬
  - 리트코드
  - depth first search
---

## Leetcode #98 - Validate Binary Search Tree

이번에는 특정 챕터별로 문제들을 풀어보겠습니다.
depth first search를 집중적으로 풀어보겠습니다.

리트코드의 문제 98 'Validate Binary Search Tree'을 파이썬으로 풀어 보도록 하겠습니다. 

discuss를 보도록 하겠습니다...
포인트는 inorder 순서로 list에 저장한 후에, 
list에서 이전 값이 현재 값보다 크거가 같으면 False, 아니면 True를 리턴하는 것입니다.

전체 코드는 아래와 같습니다.
```python
class Solution:
    # @param root, a tree node
    # @return a boolean
    def isValidBST(self, root):
        output = []
        self.inOrder(root, output)
        for i in range(1, len(output)):
            if output[i-1] >= output[i]:
                return False
        return True

    def inOrder(self, root, output):
        if root is None:
            return
        
        self.inOrder(root.left, output)
        output.append(root.val)
        self.inOrder(root.right, output)
```


시간복잡도는 O(n) : 총 n번의 inOrder 함수 호출

공간복잡도는 O(n) : n 사이즈의 list 생성
