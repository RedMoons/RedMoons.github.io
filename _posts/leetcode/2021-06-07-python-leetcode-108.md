---
title: "Leetcode Python - 108. Convert Sorted Array to Binary Search Tree"
excerpt: "Leetcode #108"

categories:
  - Python algorithm
tags:
  - algorithm
  - python
  - leetcode
  - Convert Sorted Array to Binary Search Tree
  - 알고리즘
  - 파이썬
  - 리트코드
  - bst
---

## Leetcode #108 - Convert Sorted Array to Binary Search Tree
리트코드의 문제 108 'Convert Sorted Array to Binary Search Tree'을 파이썬으로 풀어 보도록 하겠습니다. 
정렬된 list가 주어졌을 때, 이를 벨런스된 bst로 반환하는 문제입니다.

discuss를 보도록 하겠습니다...!

짚어보아야할 포인트는 linked list에서 가운데 값을 찾아 둘로 나누는 것입니다.

```python
class Solution:
    def sortedArrayToBST(self, nums):
        if not nums:
            return
        mid = len(nums)//2
        root = TreeNode(nums[mid])
        root.left = self.sortedArrayToBST(nums[:mid])
        root.right = self.sortedArrayToBST(nums[mid+1:])

        return root
```

시간복잡도는 O(n * long n) : python slice (O(n)) * log n번 수행

공간복잡도는 O(n) : n과 같은 크기의 root
