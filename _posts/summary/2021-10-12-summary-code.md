---
title: "Summary code"
excerpt: "기본 코드 정리"

categories:
  - Summary
tags:
  - summary
---

### quickSort
```python
def quickSort(arr, low, high):
    if high <= low:
        return
    mid = partition(arr, low, high)
    quickSort(arr,low, mid-1)
    quickSort(arr,mid, high)
    return arr


def partition(arr, low, high):
    pivot = arr[(low+high)//2]
    while low <= high:
        while arr[low] < pivot:
            low += 1
        while arr[high] > pivot:
            high -= 1
        if low <= high:
            arr[low], arr[high] = arr[high],arr[low]
            low += 1
            high -= 1
    return low
```
### mergeSort
```python
def mergeSort(myList):
    if not myList:
        return
    if len(myList) == 1:
        return myList
    mid = len(myList)//2
    left, right = mergeSort(myList[:mid]), mergeSort(myList[mid:])
    return merge(myList, left, right)

def merge(myList,left, right):
    i,j = 0,0
    k = 0
    while i < len(left) and j < len(right):
        if left[i] < right[j]:
            myList[k] = left[i]
            i += 1
        else:
            myList[k] = right[j]
            j += 1
        k += 1
    while i < len(left):
        myList[k] = left[i]
        k += 1
        i += 1
    while j < len(right):
        myList[k] = right[j]
        k += 1
        j += 1
    return myList
```
```python
def searchTree(root):
    res = []
    stack = [root]
    while stack:
        node = stack.pop()
        res.append(node.val)
        stack.append(node.right)
        stack.append(node.left)
    return res
```

### dfs
```python
### 1 ###
def permute(self, nums):
    res = []
    self.dfs(nums, [], res)
    return res

def dfs(self, nums, r, res):
    if not len(nums):
        res.append(r)
        return
    for i in range(len(nums)):
        self.dfs(nums[0:i] + nums[i+1], r + [nums[i]], res)

### 2 ###
def dfs(course, visited):
    if course in visited:
        return False
    if preMap[course] == []:
        return True
    
    visited.add(course)
    for c in preMap[course]:
        if not dfs(c, visited):
            return False
    visited.remove(course)
    preMap[course] = []
    return True

preMap = dict()
for i in range(numCourses):
    preMap[i] = []

for c, pre in prerequisites:
    preMap[c] = preMap.get(c, []) + [pre]

visited = set()
for c in range(numCourses):
    if not dfs(c, visited):
        return False
return True
```

# binary search
```python
def search(nums, target):
    low, high = 0, len(nums)-1
    while low <= high:
        mid = (low+high)//2
        if nums[mid] == target:
            return True
        elif nums[mid] < target:
            low = mid+1
        elif target < nums[mid]:
            high = mid-1
    return False

# dfs
def searchTree(root):
    res = []
    stack = [root]
    while stack:
        node = stack.pop()
        res.append(node.val)
        stack.append(node.right)
        stack.append(node.left)
    return res

# bfs
def searchTree(root):
    res = []
    queue = [root]
    while queue:
        node = queue.pop(0)
        res.append(node.val)
        stack.append(node.left)
        stack.append(node.right)
    return res
```

# dfs left, right 이진트리 아래부터 올라오는 예제
```python
    def distributeCoins(self, root: Optional[TreeNode]) -> int:
        def dfs(root):
            if not root:
                return 0

            left = dfs(root.left)
            right = dfs(root.right)
            self.res += abs(left) + abs(right)
            return root.val + left + right - 1
        dfs(root)
        return self.res
```

# minheap
```python
# heapify : O(n)
# pop : O(1)
# add : O(1)
# insert : O(log n)
# remove : O(log n)

def kClosest(self, points: List[List[int]], k: int) -> List[List[int]]:
    minheap = []
    for x,y in points:
        dist = x**2 + y**2
        minheap.append([dist, x, y])

    heapq.heapify(minheap)
    res = []
    while k>0:
        dist, x, y = heapq.heappop(minheap)
        res.append([x,y])
        k -= 1
```

# 이진 트리 공통 부모 찾기
```python
    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
        if p == root or q == root:
            return root
        
        left = right = None
        
        if root.left:
            left = self.lowestCommonAncestor(root.left, p, q)
        if root.right:
            right = self.lowestCommonAncestor(root.right, p, q)
            
        if left and right:
            return root
        else:
            return left or right
```

# binary search
```python
def binary_search(array) -> int:
    def condition(value) -> bool:
        pass

    left, right = min(search_space), max(search_space) # could be [0, n], [1, n] etc. Depends on problem
    while left < right:
        mid = (right + left) // 2
        if condition(mid):
            right = mid
        else:
            left = mid + 1
    return left


def binary_search(arr: List[int], target: int) -> int:
    left, right = 0, len(arr) - 1
    first_true_index = -1
    while left <= right:
        mid = (left + right) // 2
        if feasible(mid):
            first_true_index = mid
            right = mid - 1
        else:
            left = mid + 1

    return first_true_index
```
