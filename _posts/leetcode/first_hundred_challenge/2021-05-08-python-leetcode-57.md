---
title: "Leetcode Python - 57. Insert Interval"
excerpt: "Leetcode #57"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Insert Interval
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #57 - Insert Interval
리트코드의 문제 57 'Insert Intervals'을 파이썬으로 풀어 보도록 하겠습니다. 

이 문제는 주어진 list에서 새로운 newInterval을 보고 기존 interval에 더 하는 문제입니다.
```python
# 예시
Input: intervals = [[1,3],[6,9]], newInterval = [2,5]
Output: [[1,5],[6,9]]
```
[2,5]는 [1,3]과 겹치기 때문에 [1,5]로 바뀌고, [6,9]는 그대로 출력됩니다.

discuss의 답안을 보도록 하겠습니다.
left와 right를 구한 뒤에, merge 할 부분을 계산해 더해주었습니다.

```python
class Solution:
    def insert(self, intervals, newInterval):
        if len(intervals) == 0:
            return [newInterval]
        
        left = [i for i in intervals if i[1] < newInterval[0]]
        right = [i for i in intervals if i[0] > newInterval[1]]
        s = newInterval[0]
        e = newInterval[1]
        if left + right != intervals:
            s = min(newInterval[0], intervals[len(left)][0])
            e = max(newInterval[1], intervals[len(intervals)-len(right)-1][1])

        return left + [[s,e]] + right
```

left는 newInterval의 시작보다 끝값이 작을 때까지 값들을 더해주고,
right은 newInterval의 끝보다 시작값이 클 때까지 값들을 더해줍니다.

그 이후, merge 부분의 s와 e를 구해 더해주면 됩니다.


시간복잡도는 O(n) : for loop를 한번 씩 2번

공간복잡도는 O(n) : left, right 모두 전체 list보다 작음
