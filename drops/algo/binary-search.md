# Binary Search

**Category**: `algo`  
**Difficulty**: `1`  
**Read Time**: `30s`  
**Tags**: #search #divide-conquer #logn

---

## What
Find element in sorted array by halving search space. O(log n).

## Why It Exists
Linear search is O(n). For sorted data, we can do exponentially better.

## How It Works
1. Check middle element
2. If target < middle → search left half
3. If target > middle → search right half
4. Repeat until found or range empty

## Code
```python
def binary_search(arr, target):
    left, right = 0, len(arr) - 1
    
    while left <= right:
        mid = left + (right - left) // 2
        
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    
    return -1
```

## The Gotcha
Integer overflow in `(left + right) // 2` when left+right > MAX_INT (C/Java). Use `left + (right - left) // 2`.

## Real-World Example
Database queries, IP range lookups in firewalls, Git bisect.

## Micro Challenge
How to find the **first** occurrence if there are duplicates?

---

**Related**: []  
**Next**: [Binary Search Variations]
