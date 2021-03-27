---
title: "Leetcode Python - 49. Group Anagrams"
excerpt: "Leetcode #49"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Group Anagrams
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #49 - Group Anagrams
리트코드의 문제 49 'Group Anagrams'을 파이썬으로 풀어 보도록 하겠습니다. 

이 문제는 string list를 받아서 같은 Anagram 끼리 list를 만든 후 list 조합을 리턴하는 문제입니다.
Anagram은 같은 알파벳으로 이루어진 순서가 다른 조합들입니다.
예를 들어, 'abc'와 'bca'는 같은 Anagram 입니다.

discuss에서 해답을 보도록 하겠습니다.

dictionary 형태로 key-value 를 이용해서 풀었습니다.
key로 정렬된 tuple 형태로 받고, value에 해당 word를 계속 append 했습니다.

```python
key = tuple(sorted(s))
# 'abc' case 
# key = ('a', 'b', 'c')

# 'cba' case 
# key = ('a', 'b', 'c')
```

전체 코드는 아래와 같습니다.
```python
class Solution:
    def groupAnagrams(self, strs):
        d = {}
        for s in strs:
            key = tuple(sorted(s))
            d[key] = d.get(key, []) + [s]
        return list(d.values())
```

시간복잡도는 O(n) : 하나의 loop만 돈다.

공간복잡도는 O(n) : loop 돌 때, w와 key를 선언
