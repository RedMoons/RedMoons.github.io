---
title: "Leetcode Python - 31. Next Permutation"
excerpt: "Leetcode #31"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Next Permutation
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #31 - Next Permutation
리트코드의 31 문제 'Next Permutation'을 파이썬으로 풀어 보도록 하겠습니다. 

int형 list를 받아서, 그 다음 순열을 리턴하는 문제입니다.
[1,2,3]을 받으면 그 다음 큰 숫자인 [1,3,2]을 반환하면 됩니다.

discuss를 들어가서 깔끔하게 푼 답안을 보겠습니다.

먼저, 어느 지점에서 숫자를 바꾸어야하는지 알기 위해, 일의 자리부터 쭉 위로 가면서 커지다가 작아지는 지점을 찾습니다.
```python
    i = j = len(nums)-1
    while i > 0 and nums[i-1] >= nums[i]:
        i -= 1 
```
여기서 만약 i가 0이라면 숫자가 오름차순으로 정렬된 것이므로 거꾸로 정렬해주면됩니다.
```python
    if i == 0:
        nums.reverse()
        return
```
그 다음으로, 다음 큰 수로 바꾸기 위해, 그 다음 큰 수를 아래서 부터 찾습니다.
```python
    k = i - 1
    while nums[j] <= nums[k]:
        j -= 1
    nums[k], nums[j] = nums[j], nums[k]  
```
그러고 나서, 오름차순 되어있는 아래 부분을 내림차순으로 정렬해 줍니다.
```python
    l, r = k+1, len(nums)-1
    while l < r:
        nums[l], nums[r] = nums[r], nums[l]
        l +=1 ; r -= 1
```

전체 코드는 아래와 같습니다.
```python
def nextPermutation(self, nums):
    i = j = len(nums)-1
    while i > 0 and nums[i-1] >= nums[i]:
        i -= 1
    if i == 0:
        nums.reverse()
        return 
    k = i - 1
    while nums[j] <= nums[k]:
        j -= 1
    nums[k], nums[j] = nums[j], nums[k]  
    l, r = k+1, len(nums)-1
    while l < r:
        nums[l], nums[r] = nums[r], nums[l]
        l +=1 ; r -= 1
```

시간복잡도는 O(n) : while문이 하나씩만 쓰임,
공간복잡도는 O(n) : 상수 i,j,k,l,r이 선언