---
title: "Leetcode Python - 109. Convert Sorted List to Binary Search Tree"
excerpt: "Leetcode #109"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Convert Sorted List to Binary Search Tree
  - 알고리즘
  - 파이썬
  - 리트코드
  - bst
---

## Leetcode #109 - Convert Sorted List to Binary Search Tree
리트코드의 문제 109 'Convert Sorted List to Binary Search Tree'을 파이썬으로 풀어 보도록 하겠습니다. 
정렬된 linked list가 주어졌을 때, 이를 벨런스된 bst로 반환하는 문제입니다.

discuss를 보도록 하겠습니다...!

짚어보아야할 포인트는 linked list에서 가운데 값을 찾아 둘로 나누는 것입니다.

```python
class Solution:
    def sortedListToBST(self, head):
        if not head:
            return
        if not head.next:
            return TreeNode(head.val)

        slow, fast = head, head.next.next
        while fast and fast.next:
            fast = fast.next.next
            slow = slow.next
        mid = slow.next
        root = TreeNode(mid.val)
        slow.next = None
        root.left = self.sortedListToBST(head)
        root.right = self.sortedListToBST(mid.next)
        
        return root
```

시간복잡도는 O(n) : n 갯수만큼 sortedListToBST 실행

공간복잡도는 O(n) : n과 같은 크기의 root
