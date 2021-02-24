---
title: "Leetcode Python - Letter Combinations of a Phone Number"
excerpt: "Leetcode #17"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Letter Combinations of a Phone Number
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #17 - Letter Combinations of a Phone Number
리트코드의 17번 문제 'Letter Combinations of a Phone Number'을 파이썬으로 풀어 보도록 하겠습니다. 
input으로 숫자 string이 오면 가능한 전화벨의 영어 조합을 list로 반환하는 문제입니다.

먼저 숫자와 영어의 조합을 dictionary로 표현해 줍니다.
```python
        dic={
        '2':'abc',
        '3':'def',
        '4':'ghi',
        '5':'jkl',
        '6':'mno',
        '7':'pqrs',
        '8':'tuv',
        '9':'wxyz'
        }
```

그러고 결과물을 받을 ```res=['']```와 일시적으로 결과값을 받을 ```cur```을 선언해줍니다. 
여기서 포인트는 for문으로 digits을 loop하면서 res에 append를 해줍니다.

이 ```append```함수를 쓰면 리스트 요소에 더할 수가 있습니다.
```python
        res = ['']
        for digit in digits:
            cur = list()
            
            for up in dic[digit]:
                for pre in res:
                    cur.append(pre + up)
            res = cur
```
이러면 ```res```안에 모든 조합을 넣을 수 있습니다.

최종적으로는,
```python
class Solution:
    def letterCombinations(self, digits: str) -> List[str]:
        dic={
        '2':'abc',
        '3':'def',
        '4':'ghi',
        '5':'jkl',
        '6':'mno',
        '7':'pqrs',
        '8':'tuv',
        '9':'wxyz'
        }

        if len(digits) == 0:
            return []
        elif len(digits) == 1:
            return dic[digits]

        res = ['']
        for digit in digits:
            cur = list()
            
            for up in dic[digit]:
                for pre in res:
                    cur.append(pre + up)
            res = cur
        return res
```


```0 <= digits.length <= 4``` 이고, digits은 2와 9사이의 숫자이므로,

시간복잡도는 O(N)에 해결되고, (첫째 for는 최대 4, 두번째 for는 3이나 4, 세번째 for는 최대 4 * 4 * 3 = 48)
공간복잡도도 O(N)이 됩니다. (res를 가지고 있음)