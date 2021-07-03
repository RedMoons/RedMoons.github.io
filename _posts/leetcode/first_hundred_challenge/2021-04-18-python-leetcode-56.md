---
title: "Leetcode Python - 56. Merge Intervals"
excerpt: "Leetcode #56"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Merge Intervals
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #56 - Merge Intervals
리트코드의 문제 56 'Merge Intervals'을 파이썬으로 풀어 보도록 하겠습니다. 

이 문제는 주어진 list에서 내부에 list들의 조합으로 이루어져 있는데,
예시 
```
intervals = [[1,3],[2,6],[8,10],[15,18]]
```
여기서 내부 list는 start와 end를 나타냅니다.
이 list들의 겹치는 값들을 병합하는 문제입니다.

예를 보면, 두 list를 병합하는 걸 볼 수 있습니다.
As-Is
  ```
  [1,3],[2,6]
  ``` 
To-Be
  ```
  [1,6]
  ```

discuss의 답안을 보도록 하겠습니다.
정말 심플하게 풀었습니다.. 대단하십니다..

결과 값을 받을 list를 선언해 주고,
만약 현재 start보다 마지막 interval list의 end가 작다면 append 해줍니다.
그리고 아니라면 마지막 interval list의 end를 최고 값으로 변경해줍니다.

```python
class Solution:
    def merge(self, intervals):
        if len(intervals) == 1:
            return intervals

        res = []
        intervals.sort(key=lambda a: a[0])

        for i in intervals:
            if not res or res[-1][-1] < i[0]:
                res.append(i)
            else:
                res[-1][-1] = max(res[-1][-1], i[-1])
        return res
```

시간복잡도는 O(nlogn) : sort의 시간복잡도

공간복잡도는 O(n) : 최악의 경우 intervals와 동일한 res
