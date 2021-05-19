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





binary search를 이용해 풀 수 있습니다.
```python
class Solution:
    def search(self, nums, target):
        
        low, high = 0, len(nums)-1
        while low <= high:
            mid = (low+high)//2
            while low < mid and nums[low] == nums[mid]:
                low += 1
            while mid < high and nums[high] == nums[mid]:
                high -= 1
            if nums[mid] == target:
                return True
            if nums[low] <= nums[mid]:
                if nums[low] <= target < nums[mid]:
                    high = mid-1
                else:
                    low = mid+1
            else:
                if nums[mid] < target <= nums[high]:
                    low = mid+1
                else:
                    high = mid-1
        return False
```

여기서 눈여겨 볼 것은 중복되는 값들을 제거하기 위해, 아래와 같이 low,high를 더하고 빼줍니다.
```python
while low < mid and nums[low] == nums[mid]:
    low += 1
while mid < high and nums[high] == nums[mid]:
    high -= 1
```

시간복잡도는 O(log n) : binary search

공간복잡도는 O(1) : low,mid,high 선언
