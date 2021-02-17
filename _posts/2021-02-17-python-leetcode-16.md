---
title: "Leetcode Python - 3Sum Closest"
excerpt: "Leetcode #16"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - 3Sum Closest
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #16 - 3Sum Closest
리트코드의 16번 문제 '3Sum Closest'을 파이썬으로 풀어 보도록 하겠습니다. 
이 문제는 주어진 list에서 3개 값의 합이 target과 가장 비슷한 값을 리턴하는 문제입니다.
[https://leetcode.com/problems/3sum-closest/](https://leetcode.com/problems/3sum-closest/)


처음에는, list를 정렬해주고 ret의 초기값을 정해주고, list를 for문으로 돌면서 left와 right를 포인터로 하여 비교해 줍니다. 
```python
nums.sort()
ret = nums[0]+nums[1]+nums[len(nums)-1]
for i in range(len(nums)):
    l, r = i+1, len(nums)-1
```

그리고, l과 r을 이동시키면서 합을 구해줍니다.
```python
for i in range(len(nums)):
    l, r = i+1, len(nums)-1
    while l < r:
        s = nums[i]+nums[l]+nums[r]
```

다음 target과 s를 비교해야하는데, 여기서 음수가 나올 수 있으므로 ```abs```함수로 절대값을 비교해줍니다. 절대값이 작을 경우 ret을 변경해 줍니다.

또한, target이 s보다 작을 경우, s가 작아져야하므로 r을 줄여주고, 반대경우에는 반대로 해줍니다.
최종 코드는 이렇습니다.
```python
class Solution:
    def threeSumClosest(self, nums: List[int], target: int) -> int:
        if len(nums) == 3:
            return sum(nums)
        nums.sort()
        
        ret = nums[0]+nums[1]+nums[len(nums)-1]
        
        for i in range(len(nums)):
            l, r = i+1, len(nums)-1
            while l < r:
                s = nums[i]+nums[l]+nums[r]
                if abs(ret-target) > abs(s-target):
                    ret = s
                if target < s:
                    r -= 1
                else:
                    l += 1
        return ret
```

시간복잡도는 O(n²)
공간복잡도는 O(1)
<br>

---
#### 개선하기
여기서 discuss를 참고해서 개선할 수 있는 부분은
1. sum 함수 이용하기
* AS-IS
    ```python
    ret = nums[0]+nums[1]+nums[len(nums)-1] 
    ```
* TO-BE
    ```python
    ret = sum[:3]
    ```
<br>

* AS-IS
    ```python
    s = nums[i]+nums[l]+nums[r]
    ```
* TO-BE
    ```python
    s = sum(nums[i], nums[l], nums[r])
    ```

이러면 조금 더 예쁘게 작성할 수 있다.

