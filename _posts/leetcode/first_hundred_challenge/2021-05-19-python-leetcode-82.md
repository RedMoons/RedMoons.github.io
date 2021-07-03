---
title: "Leetcode Python - 82. Remove Duplicates from Sorted List II"
excerpt: "Leetcode #82"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Remove Duplicates from Sorted List II
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #82 - Remove Duplicates from Sorted List II
리트코드의 문제 82 'Remove Duplicates from Sorted List II'을 파이썬으로 풀어 보도록 하겠습니다. 

주어진 linked list에서 중복된 숫자를 제거한 linked list를 반환하는 문제입니다.
solution을 보면 sentinel node를 통해 풀 수 있습니다.
일종의 header앞에 dummy node를 두는 형식입니다.

header를 계속 앞으로 진행해 나가면서, next와 같은 값이 나온다면 pred를 앞으로 진행해 나가면서 해결합니다.
```python
class Solution:
    def deleteDuplicates(self, head):

        sentinel = ListNode(0,head)
        pred = sentinel
        while head:
            if head.next and head.val == head.next.val:
                while head.next and head.val == head.next.val:
                    head = head.next
                pred.next = head.next
            else:
                pred = pred.next
            head = head.next
        return sentinel.next
```


시간복잡도는 O(n) : linked list 를 loop 한 바퀴

공간복잡도는 O(1) : sentinel, pred 선언
