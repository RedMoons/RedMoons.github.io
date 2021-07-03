---
title: "Leetcode Python - 92. Reverse Linked List II"
excerpt: "Leetcode #92"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Reverse Linked List II
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #92 - Reverse Linked List II
리트코드의 문제 92 'Reverse Linked List II'을 파이썬으로 풀어 보도록 하겠습니다. 
linked list가 주어지면, left에서 right까지의 노드를 reverse한 결과를 반환하는 문제입니다.

discuss를 보도록 하겠습니다.
dummy node를 생성해 head 앞에 넣고, prev와 cur를 left이전과 left를 point합니다.
이후 reverse node로 바꾸어주고 값을 설정해주면 됩니다.

처음 dummy node를 생성해줍니다.
```python
dummy = ListNode(0)
dummy.next = head
```

cur와 prev를 세팅해줍니다.
```python
cur, prev = head, dummy
for _ in range(m - 1):
    cur = cur.next
    prev = prev.next
```

temp를 선언해 reverse node list를 만들어 줍니다.
```python
for _ in range(n - m):
    temp = cur.next
    cur.next = temp.next
    temp.next = prev.next
    prev.next = temp
```


시간복잡도는 O(n) : 크기 n loop를 한 번씩

공간복잡도는 O(1) : cur, prev, temp 선언
