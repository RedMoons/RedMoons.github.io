---
title: "Leetcode Python - 213. House Robber II"
excerpt: "Leetcode #213"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - House Robber II
  - 알고리즘
  - 파이썬
  - 리트코드
  - dynamic programming
---

## Leetcode #213 - House Robber II

이번에는 특정 챕터별로 문제들을 풀어보겠습니다.
dynamic programming를 집중적으로 풀어보겠습니다.

리트코드의 문제 213 'House Robber II'을 파이썬으로 풀어 보도록 하겠습니다. 
이 문제는 주어진 List에서 연속되지 않은 index들의 최대 합을 구하는 문제입니다.

discuss를 보도록 하겠습니다! ^^ 

포인트는 k번째의 최대값은 f(k-2) + nums[k] 혹은 f(k-1) 중에 최대값 인 것입니다.
```python
f(k) = max( f(k-2) + nums[k], f(k-1) )
```

둘째로는, 맨 앞과 맨 뒤를 동시에 도둑질 할 수 없기 때문에, 
max를 아래와 같이 구해 줍니다.
```python
max(f(nums[1:]), f(nums[:-1]))
```

전체 코드는 아래와 같습니다.
### dp list를 이용한 버전
```python
class Solution:
    def rob(self, nums):
        
        def get_max_rob(nums):
            dp = [0 for _ in range(len(nums))]
            dp[0] = nums[0]
            dp[1] = max(nums[0], nums[1])
            for i in range(2, len(nums)):
                dp[i] = max(dp[i-2]+nums[i], dp[i-1])
            return dp[-1]
    
        if not nums:
            return
        if len(nums) == 1:
            return nums[0]
        elif len(nums) == 2:
            return max(nums)
            
        return max(get_max_rob(nums[1:]), get_max_rob(nums[:-1]))
```

시간복잡도는 O(n) : nums loop

공간복잡도는 O(n) : nums 사이즈의 dp list


### dp 변수만을 이용한 버전
```python
class Solution:
    def rob(self, nums):
        def get_max_rob(nums):
            dp1, dp2 = 0, 0
            for num in nums:
                dp1, dp2 = dp2, max(dp1+num,dp2)
            return dp2
    
        if not nums:
            return
        if len(nums) == 1:
            return nums[0]
        elif len(nums) == 2:
            return max(nums)
            
        return max(get_max_rob(nums[1:]), get_max_rob(nums[:-1]))
```

시간복잡도는 O(n) : nums loop

공간복잡도는 O(1) : 변수 dp1,dp2 선언

