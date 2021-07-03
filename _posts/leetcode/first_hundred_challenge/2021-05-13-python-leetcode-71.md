---
title: "Leetcode Python - 71. Simplify Path"
excerpt: "Leetcode #71"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Simplify Path
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #71 - Simplify Path
리트코드의 문제 71 'Simplify Path'을 파이썬으로 풀어 보도록 하겠습니다. 

이 문제는 리눅스의 path가 input으로 주어지면, 해당 path의 단순 버전을 output하는 문제입니다.

예를 들어 아래와 같습니다.
```bash
Input: path = "/a/./b/../../c/"
Output: "/c"
```

먼저, ```/```나 ```//``` (슬래시, 더블 슬래시)가 아닌 ```///```(세개 혹은 세개 이상)의 경우 없애줍니다.
```python
p = [i for i in path.split('/') if i]
```

그 후에 loop를 돌면서 ```.``` 경우에는 continue, 
```..``` 경우 list의 pop을 해줍니다.

전체 코드는 아래와 같습니다.
```python
class Solution:
    def simplifyPath(self, path):
        p = [i for i in path.split('/') if i]
        
        t = []
        for i in range(len(p)):
            if p[i] == '.' :
                continue
            if p[i] == '..':
                if len(t)>0:
                    t.pop()
                continue
            t.append(p[i])
        r = '/' + '/'.join(t)
        return r
```


시간복잡도는 O(n) : loop 한번

공간복잡도는 O(n) : 최악의 경우 p=path, t=path 이므로 2n
