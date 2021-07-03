---
title: "Leetcode Python - 75. Sort Colors"
excerpt: "Leetcode #75"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Sort Colors
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #75 - Sort Colors
리트코드의 문제 75 'Sort Colors'을 파이썬으로 풀어 보도록 하겠습니다. 

이 문제는 list가 주어지면, 크기별로 순서대로 정렬하는 문제입니다.

저는 count라는 dictionary를 선언해 0,1,2의 숫자를 업데이트하고, 
이 갯수만큼 nums를 업데이트 해줍니다.

```python
class Solution:
    def sortColors(self, nums):
        count = {'0':0, '1':0, '2':0}
        n = len(nums)

        for i in range(n):
            if nums[i] == 0:
                count['0'] += 1
            elif nums[i] == 1:
                count['1'] += 1
            else:
                count['2'] += 1
        
        for i in range(count['0']):
            nums[i] = 0
        for i in range(count['1']):
            nums[i + count['0']] = 1
        for i in range(count['2']):
            nums[i + count['0'] + count['1']] = 2
```


시간복잡도는 O(n) : n에 대한 loop가 2번

공간복잡도는 O(1) : dictionary count 선언

