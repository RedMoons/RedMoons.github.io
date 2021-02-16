---
title: "Leetcode Python - ZigZag Conversion"
excerpt: "Leetcode #6"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - ZigZag Conversion
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #6 - ZigZag Conversion
리트코드의 6번 문제 'ZigZag Conversion'을 파이썬으로 풀어 보도록 하겠습니다. 
이 문제는 string을 ZigZag로 바꾸어서 출력하는 문제입니다.
[https://leetcode.com/problems/zigzag-conversion/](https://leetcode.com/problems/zigzag-conversion/)


discuss에 올라온 파이썬 해설을 보도록 합시다.
포인트는 첫째로 ```index```와 ```step```을 정의해서, ```index```로는 ```row```를 가리키고, ```step```은 ```1```아니면 ```-1```로 ```index```를 위로 갈지, 아래로 갈지 방향을 정해줍니다.
둘째로, ```numRows```만큼의 리스트를 만들어 각 ```row```의 값들을 append하고, 마지막에 합쳐주는 것입니다.

```python
class Solution(object):
    def convert(self, s, numRows):
        """
        :type s: str
        :type numRows: int
        :rtype: str
        """
        if numRows == 1 or numRows >= len(s):
            return s

        L = [''] * numRows
        index, step = 0, 1

        for x in s:
            L[index] += x
            if index == 0:
                step = 1
            elif index == numRows -1:
                step = -1
            index += step

        return ''.join(L)
```

예를 들어 s가 abcdefghijk이고, numRows가 3이면
처음에는 아래로 순차적으로 내려가고
```shell
L[0] : a 
L[1] : b
L[2] : c
```
다음에는 ```step=-1```이 되면서, d가 ```L[1]```에 가게 됩니다.
```shell
L[0] : ae
L[1] : bd
L[2] : c
```
이런식으로 지그재그하게 리스트에 쌓이게 됩니다.


보면서 정말 대단한 분들이 많다는걸 느끼게 됩니다..

시간복잡도는 O(n) : 하나의 for문 뿐이기 때문에 
공간복잡도는 O(n) : L[index]에 모든 값이 들어가기 때문에
