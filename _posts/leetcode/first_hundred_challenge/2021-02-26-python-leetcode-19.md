---
title: "Leetcode Python - 19. Remove Nth Node From End of List"
excerpt: "Leetcode #19"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Remove Nth Node From End of List
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #19 - Remove Nth Node From End of List
리트코드의 19번 문제 'Remove Nth Node From End of List'을 파이썬으로 풀어 보도록 하겠습니다. 

input으로 linked list의 head와 int n이 오면, 끝에서 n번째 linked list를 삭제하고 head를 리턴하는 문제입니다.

아직도 깔끔하게 짜지 못해서.. discuss로 가서 보도록 하겠습니다.

linked list에서 끝에서 n번째 노드를 삭제해야하는데, 전체 길이를 모르기 때문에, ```point```를 두 개 두었습니다.
```python
fast = slow = head
```

그리고 n만큼 fast를 이동시킵니다.
```python
for _ in range(n):
    fast = fast.next
```

여기서 fast가 None일 경우에는
n과 linked list의 길이가 같은 경우이므로 맨 앞에 head가 가리키는 노드를 삭제하면 됩니다. 
```python
if not fast:
    return head.next
```

fast에서 linked list끝까지 가는 동안, slow도 이동한 후에 slow의 next를 건너뛰고 slow.next.next로 해줍니다.
전체 길이에서 n을 뺀 수만큼 slow가 이동하기 때문에 slow 다음의 노드를 삭제해줍니다.
```python
        while fast.next:
            fast = fast.next
            slow = slow.next
        slow.next = slow.next.next
```

전체 코드는 아래와 같습니다.
```python
    def removeNthFromEnd(self, head, n):
        fast = slow = head
        for _ in range(n):
            fast = fast.next
        if not fast:
            return head.next
        while fast.next:
            fast = fast.next
            slow = slow.next
        slow.next = slow.next.next
        return head
```
