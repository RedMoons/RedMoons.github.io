---
title: "Leetcode Python - 4Sum Closest"
excerpt: "Leetcode #18"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - 4Sum Closest
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #18 - 4Sum Closest
리트코드의 18번 문제 '4Sum Closest'을 파이썬으로 풀어 보도록 하겠습니다. 
이 문제는 주어진 list에서 4개 값의 합이 target이 되는 list를 리턴하는 문제입니다.

이 문제는 discuss에서도 알 수 있듯이, 이전 #16번의 '3Sum Closest'을 응용해서 풀 수 있습니다.

nums에서 하나의 값을 뺀걸 그만큼 target에서 빼면 '3Sum Closest' 코드를 이용할 수 있습니다.
```fourSum```함수를 간력히 구현해본다면 아래처럼 구현할 수 있습니다.
```python
class Solution:
    def fourSum(self, nums: List[int], target: int) -> List[List[int]]:
        if len(nums) < 4:
            return []
        nums.sort()
        res = []

        for i in range(len(nums)-3):
            if i == 0 or nums[i] != nums[i-1]:
                threeSumRes = self.threeSum(nums[i+1:], target-nums[i])
                # e.g. threeSumRes = [[1,2,7],[1,4,5]]
                for i_ in threeSumRes:
                    res.append(i_ + [nums[i]])
        return res
```

두 번째 for구문은 threeSumRes의 내부 리스트에 i값을 더하기 위해서 입니다.

그러면 이제 ```threeSum```함수를 구현해 보겠습니다.
```python
    def threeSum(self, nums: List[int], target: int) -> List[List[int]]:
        nums.sort()
        res = []

        for i in range(len(nums)-2):
            if i == 0 or nums[i] != nums[i-1]:
                t = target - nums[i]
                l, r = i+1, len(nums)-1

                while l < r:
                    s = nums[l] + nums[r]
                    if s == t:
                        res.append([nums[i], nums[l], nums[r]])
                        while l < r and nums[l] == nums[l+1]: l += 1
                        while l < r and nums[r] == nums[r-1]: r -= 1
                        l += 1
                        r -= 1
                    elif s > t:
                        r -= 1
                    else:
                        l += 1
        return res
```

시간복잡도는 O(n³) (굉장히 비효율적인 코딩이 되었네요..)
공간복잡도는 O(1)