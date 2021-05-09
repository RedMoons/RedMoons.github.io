---
title: "Leetcode Python - 61. Rotate List"
excerpt: "Leetcode #61"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Rotate List
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #61 - Rotate List
리트코드의 문제 61 'Rotate List'을 파이썬으로 풀어 보도록 하겠습니다. 

이 문제는 linked list를 rotate 시키는 문제입니다.
discuss를 보도록 하겠습니다.. 어서 내공이 쌓여 후딱 후딱 풀 수 있는 그날이 오기를..

순서는
1. linked list의 끝을 시작점과 연결하고
2. 새롭게 시작되는 지점을 설정 및 이전 노드의 연결을 끊습니다.

먼저 last와 길이를 구하고, 시작점과 연결해줍니다.
```python
last = head
leng = 1
while last.next != None:
    last = last.next
    leng += 1
last.next = head
```

새로운 시작점 직전으로 가서 시작점 설정 및 연결을 끊습니다.
```python
k = k % leng
tmp = head
for _ in range(leng-k-1):
    tmp = tmp.next
res = tmp.next
tmp.next = None
```

전체 코드는 아래와 같습니다.
```python
class Solution:
    def rotateRight(self, head: ListNode, k: int) -> ListNode:
        if head is None:
            return head

        last = head
        leng = 1
        while last.next != None:
            last = last.next
            leng += 1

        last.next = head

        k = k % leng
        tmp = head
        for _ in range(leng-k-1):
            tmp = tmp.next
        res = tmp.next
        tmp.next = None
        return res
```


시간복잡도는 O(n) : for loop를 한번 씩 2번

공간복잡도는 O(n) : last, tmp, res 를 노드로 선언하므로 3n
