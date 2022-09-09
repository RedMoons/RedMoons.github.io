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