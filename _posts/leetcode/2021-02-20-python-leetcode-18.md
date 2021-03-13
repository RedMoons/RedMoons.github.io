---
title: "Leetcode Python - 18. 4Sum Closest"
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
공간복잡도는 O(n)

---

### 다른 풀이 참고
discuss에 나와있는 다른 풀이를 봐보겠습니다.
풀이는 아래와 같습니다.
```python
def fourSum(self, nums, target):
    def findNsum(l, r, target, N, result, results):
        if r-l+1 < N or N < 2 or target < nums[l]*N or target > nums[r]*N:
            return
        if N == 2: 
            while l < r:
                s = nums[l] + nums[r]
                if s == target:
                    results.append(result + [nums[l], nums[r]])
                    l += 1
                    while l < r and nums[l] == nums[l-1]:
                        l += 1
                elif s < target:
                    l += 1
                else:
                    r -= 1
        else:
            for i in range(l, r+1):
                if i == l or (i > l and nums[i-1] != nums[i]):
                    findNsum(i+1, r, target-nums[i], N-1, result+[nums[i]], results)

    nums.sort()
    results = []
    findNsum(0, len(nums)-1, target, 4, [], results)
    return results
```

이 풀이는 재귀를 이용하였고, twoSum을 응용했습니다.
```findNsum(l, r, target, N, result, results)``` 함수에서 input으로 left, right, target(합이 될 숫자), N은 합할 숫자들의 갯수, result는 처음 target에서 값을 하나씩 뺀 합, results는 최종 결과를 위한 변수입니다.
loop를 돌며 N을 하나씩 줄여나가면서 ```if N == 2:``` 가 될 경우 twoSum 함수를 구현하였습니다.

이 분도 대단하시네요. 저도 이렇게 깔끔하게 구현하도록 열심히 하겠습니다.

시간복잡도는 O(n³) 재귀는 함수를 부르는 만큼 시간복잡도를 더하는데, 
N=4일 때, N번 함수를 부르고,
N=3일 때, N(N-1)번 함수를 부르고,
N=2일 때, N(N-1)(N-2)번 함수를 부르므로 O(n³) 입니다.
공간복잡도는 O(n) 입니다.