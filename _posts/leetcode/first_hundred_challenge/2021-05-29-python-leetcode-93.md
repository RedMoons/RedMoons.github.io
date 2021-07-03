---
title: "Leetcode Python - 93. Restore IP Addresses"
excerpt: "Leetcode #93"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Restore IP Addresses
  - 알고리즘
  - 파이썬
  - 리트코드
  - dfs
---

## Leetcode #93 - Restore IP Addresses
리트코드의 문제 93 'Restore IP Addresses'을 파이썬으로 풀어 보도록 하겠습니다. 
string이 주어지면 valid ip인지 아닌지 체크하는 문제입니다.

valid ip 예제로 각 값들이 0에서 255사이의 수여야 합니다.
```0.1.2.201```, ```192.168.1.1```
invalid ip 예제로는
```0.011.255.245```, ```192.168.1.312```

처음에 s 길이가 작을 때 구현해줍니다.
```python
if len(s) < 4:
    return []
elif len(s) == 4:
    return ['.'.join(s)]
```

그리고 나서 dfs로 구현해줍니다.
1자리 경우, 2자리 경우, 3자리 경우를 나누어 진행합니다.

전체 코드는 아래와 같습니다.
```python
class Solution:
    def restoreIpAddresses(self, s):
        if len(s) < 4:
            return []
        elif len(s) == 4:
            return ['.'.join(s)]
        
        ret = []
        path = ''
        self.dfs(s, path, ret)
        return ret
            
    def dfs(self, s, path, ret):
        if len(s) == 0:
            if len(path.split('.')) == 5:
                ret.append(path[:-1])
            return
        if len(path.split('.')) >= 5:
            return

        self.dfs(s[1:], path+s[:1]+'.', ret)
        if s[0] != '0' and len(s)>1:
            self.dfs(s[2:], path+s[:2]+'.', ret)
        if s[0] != '0' and len(s)>2 and s[:3] < '256':
            self.dfs(s[3:], path+s[:3]+'.', ret)
```
시간복잡도는 O(n²) : sum(1~n) + sum(1~n-1) + sum(1~n-2)... n²에 수렴

공간복잡도는 O(n²) : path가 호출되는 만큼 선언
