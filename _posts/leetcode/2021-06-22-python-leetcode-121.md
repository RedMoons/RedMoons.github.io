---
title: "Leetcode Python - 121. Best Time to Buy and Sell Stock"
excerpt: "Leetcode #121"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Best Time to Buy and Sell Stock
  - 알고리즘
  - 파이썬
  - 리트코드
---

## Leetcode #121 - Best Time to Buy and Sell Stock
리트코드의 문제 121 'Best Time to Buy and Sell Stock'을 파이썬으로 풀어 보도록 하겠습니다. 
주어진 list에서 주식을 사고 팔아서 최대의 이익을 return하는 문제입니다.

maxProfit을 구해 최대가 되는 값을 return 해줍니다.

```python
class Solution:
    def maxProfit(self, prices):
        if len(prices) == 1:
            return 0
        
        maxProfit = 0
        minBuy = prices[0]
        for i in range(1, len(prices)):
            maxProfit = max(maxProfit, prices[i] - minBuy)
            minBuy = min(minBuy, prices[i])
        return maxProfit
```

시간복잡도는 O(n) : 첫번째 for loop (n)

공간복잡도는 O(1) : maxProfit과 minBuy 선언
