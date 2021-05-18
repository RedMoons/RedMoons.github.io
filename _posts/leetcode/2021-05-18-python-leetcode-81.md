---
title: "Leetcode Python - 80. Remove Duplicates from Sorted Array II"
excerpt: "Leetcode #80"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Remove Duplicates from Sorted Array II
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #80 - Remove Duplicates from Sorted Array II
리트코드의 문제 80 'Remove Duplicates from Sorted Array II'을 파이썬으로 풀어 보도록 하겠습니다. 

주어진 list에서 연속된 2개의 중복만 허용하고, 3번째부터는 제거된 list를 만들고, 최종 list의 길이를 반환하는 문제입니다.

cnt, idx를 선언하여 풀었습니다.
```python
class Solution:
    def removeDuplicates(self, nums):
        cnt, idx = 1, 1
        while idx < len(nums):
            cnt = cnt + 1 if nums[idx] == nums[idx-1] else 1
            if cnt == 3:
                nums.pop(idx)
                idx -= 1
                cnt -= 1
            idx += 1
        return len(nums)
```


시간복잡도는 O(n) : loop 한 번

공간복잡도는 O(1) : idx,cnt 상수 선언, list pop함수 호출

