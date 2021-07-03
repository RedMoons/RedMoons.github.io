---
title: "Leetcode Python - 24. Swap Nodes in Pairs"
excerpt: "Leetcode #24"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Swap Nodes in Pairs
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #24 - Swap Nodes in Pairs
리트코드의 24번 문제 'Swap Nodes in Pairs'을 파이썬으로 풀어 보도록 하겠습니다. 

이 문제는 linked list를 받아서 2쌍씩 앞뒤를 바꾸는 문제입니다.

예전에 풀었던 linked list문제를 참고 해서 풀었습니다.
궁금하다면 이 [링크](https://redmoons.github.io/python%20algorithm/python-leetcode-19/)를 봐보세요.

먼저, 비어있거나 node가 1 개인 경우 head를 리턴해줍니다.
```python
if head == None or head.next == None:
    return head
```

그러고 나서, fast와 slow를 포인터로 head에 선언해주고, fast와 slow의 값을 바꿔주면서 끝까지 loop를 해줍니다.
```python
fast = slow = head
fast = fast.next
v = 0
while fast:
    v = slow.val
    slow.val = fast.val
    fast.val = v

    if fast.next == None:
        break
    fast = fast.next.next
    slow = slow.next.next
```

전체 코드는 아래와 같습니다.
```python
class Solution:
    def swapPairs(self, head: ListNode) -> ListNode:
        if head == None or head.next == None:
            return head

        fast = slow = head
        fast = fast.next
        v = 0
        while fast:
            v = slow.val
            slow.val = fast.val
            fast.val = v

            if fast.next == None:
                break
            fast = fast.next.next
            slow = slow.next.next
        return head
```

시간복잡도는 O(n) : linked list를 한 바퀴 loop,
공간복잡도는 O(n) : loop하면서 fast, slow, v를 저장

-----
#### 개선 해보기

discuss에 가서 다른 풀이를 보도록 하겠습니다.

먼저, dummy node 하나와 pre node를 두고, pre를 head 앞으로 둡니다.
```python
dummy = pre = ListNode(0)
pre.next = head
```

a를 앞의 노드, b를 뒤의 노드로 서로 바꾸어줍니다. 그리고 dummy.next를 리턴해 주면 끝!입니다.
```python
while pre.next and pre.next.next:
    a = pre.next
    b = a.next
    pre.next, a.next, b.next = b, b.next, a
    pre = a
return dummy.next
```

전체코드는
```python
class Solution:
    def swapPairs(self, head):
        dummy = pre = ListNode(0)
        pre.next = head
        while pre.next and pre.next.next:
          a = pre.next
          b = a.next
          pre.next, a.next, b.next = b, b.next, a.next
          pre = a
        return dummy.next
```

시간복잡도는 O(n) : loop 한번이므로,
공간복잡도는 O(n) : loop 돌면서 a,b,pre를 할당