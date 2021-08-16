---
title: "Leetcode Python - 116. Populating Next Right Pointers in Each Node"
excerpt: "Leetcode #116"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Populating Next Right Pointers in Each Node
  - 알고리즘
  - 파이썬
  - 리트코드
  - depth first search
---

## Leetcode #116 - Populating Next Right Pointers in Each Node

이번에는 특정 챕터별로 문제들을 풀어보겠습니다.
depth first search를 집중적으로 풀어보겠습니다.

리트코드의 문제 116 'Populating Next Right Pointers in Each Node'을 파이썬으로 풀어 보도록 하겠습니다. 

discuss를 보도록 하겠습니다..

포인트는 root의 next가 존재하면 root.right.next를 root.next.left로 세팅하는 것입니다.

전체 코드는 아래와 같습니다.
```python
class Solution:
    def connect(self, root: 'Node') -> 'Node':
        if root and root.left and root.right:
            root.left.next = root.right
            if root.next:
                root.right.next = root.next.left
            self.connect(root.left)
            self.connect(root.right)
        return root
```

시간복잡도는 O(n) : n개의 node를 방문

공간복잡도는 O(1) : in place 



dfs를 이용해 풀 수도 있습니다.

```python
class Solution:
    def connect(self, root: 'Node') -> 'Node':
        if not root:
            return
        stack = [root]
        while stack:
            node = stack.pop()
            if node.left and node.right:
                node.left.next = node.right
                if node.next:
                    node.right.next = node.next.left
                stack.append(node.right)
                stack.append(node.left)
        return root
```

시간복잡도는 O(n) : node의 모든 값들을 방문

공간복잡도는 O(n) : stack에 최대 n/2 크기 list 생성
