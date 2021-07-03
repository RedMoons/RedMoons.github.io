---
title: "Leetcode Python - Two Sum"
excerpt: "Leetcode #1"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - two sum
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #1 - Two Sum
리트코드의 1번 문제 'Two Sum'을 파이썬으로 풀어 보도록 하겠습니다. 
이 문제는 int 리스트에서 2개의 합이 타켓 int 가 되게 하는 것입니다.
[https://leetcode.com/problems/two-sum/](https://leetcode.com/problems/two-sum/)


첫 번째로 brute-force 방식으로 하나하나씩 구해보겠습니다.
그러기 위해서는 리스트에서 2개의 합을 구해야 하므로, 이중 for loop를 돌면서 두 개의 합이 타켓과 일치할 때 리턴해주면 됩니다.

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for i in range(0,len(nums)-1):
            for _i in range(i+1, len(nums)):
                if(nums[i] + nums[_i] == target):
                    return [i,_i]
```

> 시간 복잡도는 O(n²) : 2중 for loop를 이용, 공간 복잡도는 O(1)  : i 와 _i만이 선언되었으니 상수

결과는 아래와 같습니다.
> Runtime: 48 ms,
> Memory Usage: 14.4 MB

<br>

---
이 결과를 개선하기 위해 이렇게 해봅시다.
중복된 값이 안 나온다고 하였으므로, list를 dictionary로 바꾸어서 (key는 list의 값들로, value는 index로) for loop를 한 번으로 줄여 보겠습니다.
```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        dic = {}
        i = 0
        for v in nums:
            dic[v] = i
            i += 1
        for _i in range(len(nums)):
            if target - nums[_i] in dic and dic[target - nums[_i]] != _i:
                return [dic[target-nums[_i]], _i]
```

> Runtime: 64 ms
Memory Usage: 14.6 MB

runtime이 이중 for loop보다 더 오래나오는군요..

<br>

discuss탭으로 가서 O(n)으로 구현한 것이 있어 봐보겠습니다.
```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        d = {}
        for i,n in enumerate(nums):
            m = target - n
            if m in d:
                return [d[m],i]
            else:
                d[n] = i
```
먼저, enumerate를 이용해 index i와 value n을 선언하고, target에서 n을 뺀 나머지를 d에서 찾는 로직입니다.
확실히 이렇게 구현할 경우 O(n)으로 구현이 가능합니다.

> 시간복잡도 : O(n)
공간복잡도 : O(1)
