---
title: "Leetcode Python - 86. Partition List"
excerpt: "Leetcode #86"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Partition List
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #86 - Partition List
리트코드의 문제 86 'Partition List'을 파이썬으로 풀어 보도록 하겠습니다. 

주어진 linked list에서 x 보다 작은 수의 경우 x 보다 왼쪽으로 이동시키는 문제입니다.
solution을 보도록 하겠습니다.

2 pointer approach로 풀 수 있습니다.

2 pointer를 선언해줍니다.
```python
p1 = h1 = ListNode(0)
p2 = h2 = ListNode(0)
```

그 후 loop를 돌면서, x 보다 작으면 p1으로, 크면 p2로 linked list를 구현합니다.
```python
while head:
    if head.val < x:
        p1.next = head
        p1 = p1.next
    else:
        p2.next = head
        p2 = p2.next
    head = head.next
```

마지막으로 p1과 p2를 연결해줍니다.
```python
p1.next = h2.next
p2.next = None
return h1.next
```

전체 함수는 아래와 같습니다.
```python
class Solution:
    def partition(self, head, x):
       
        p1 = h1 = ListNode(0)
        p2 = h2 = ListNode(0)
        
        while head:
            if head.val < x:
                p1.next = head
                p1 = p1.next
            else:
                p2.next = head
                p2 = p2.next
            head = head.next
        
        
        p1.next = h2.next
        p2.next = None
        return h1.next
```

시간복잡도는 O(n) : linked list 를 loop 한 바퀴

공간복잡도는 O(1) : p1,p2,h1,h2 선언
