---
title: "Leetcode Python - 2. Add Two Numbers"
excerpt: "Leetcode #2"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Add Two Numbers
  - 알고리즘
  - 파이썬
  - 리트코드
  - linkedlist
---

## Leetcode #2 - Add Two Numbers

이번에는 특정 챕터별로 문제들을 풀어보겠습니다.
linkedlist를 집중적으로 풀어보겠습니다.

리트코드의 문제 2 'Add Two Numbers'을 파이썬으로 풀어 보도록 하겠습니다. 

discuss를 보도록 하겠습니다..

포인트는 dummy와 cur ListNode를 만들어 새로운 linked list를 만드는 것입니다.

전체 코드는 아래와 같습니다.
```python
class Solution:
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        dummy = cur = ListNode(val=0)
        carry = 0
        while l1 or l2 or carry:
            v1,v2 = 0,0
            if l1:
                v1 = l1.val
                l1 = l1.next
            if l2:
                v2 = l2.val
                l2 = l2.next
            cur.next = ListNode(val=(v1+v2+carry)%10)
            carry = (v1+v2+carry)//10
            cur = cur.next
        return dummy.next
```

시간복잡도는 O(n) : n개의 node를 방문

공간복잡도는 O(n) : n크기의 linked list를 만듦



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
