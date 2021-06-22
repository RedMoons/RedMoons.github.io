---
title: "Leetcode Python - 122. Best Time to Buy and Sell Stock II"
excerpt: "Leetcode #122"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Best Time to Buy and Sell Stock II
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #122 - Best Time to Buy and Sell Stock II
리트코드의 문제 122 'Best Time to Buy and Sell Stock II'을 파이썬으로 풀어 보도록 하겠습니다. 
주어진 list에서 주식을 사고 파는 것을 반복해 최대의 이익을 return하는 문제입니다.

discuss를 보면, 매우 단순하게 다음 element가 현재 element보다 크다면 더해 합을 return해서 풀었습니다.

```python
class Solution:
    def maxProfit(self, prices):        
        return sum([ max(prices[i+1]-prices[i], 0) for i in range(len(prices)-1)])
```
대단하게도 깔끔하게 한 줄로 해결할 수 있습니다. 

[5,6,7] 케이스를 보면
답은 7-5=2이므로 (6-5) + (7-6) 이렇게 구현이 가능합니다.

저는 같은 날에 buy, sell을 동시에 못한다고 생각했는데, 가능한 transaction이네요.

다음에는 제약 조건을 좀더 생각해 보아야 겠습니다.

시간복잡도는 O(n) : 첫번째 for loop (n)

공간복잡도는 O(n) : (n-1) 크기의 list 생성
