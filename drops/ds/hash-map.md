# Hash Map

**Category**: `ds`  
**Difficulty**: `2`  
**Read Time**: `45s`  
**Tags**: #hashing #key-value #o1-lookup

---

## What
Key-value data structure with O(1) average lookup/insert/delete.

## Why It Exists
Arrays need numeric indices. Hash maps let you use any key (strings, objects) to access values instantly.

## How It Works
1. Hash function converts key → integer index
2. Store value at array[index]
3. Handle collisions (separate chaining or open addressing)
4. Resize when load factor > threshold (~0.75)

## Code
```python
class HashMap:
    def __init__(self):
        self.size = 8
        self.buckets = [[] for _ in range(self.size)]
    
    def _hash(self, key):
        return hash(key) % self.size
    
    def put(self, key, value):
        idx = self._hash(key)
        for i, (k, v) in enumerate(self.buckets[idx]):
            if k == key:
                self.buckets[idx][i] = (key, value)
                return
        self.buckets[idx].append((key, value))
    
    def get(self, key):
        idx = self._hash(key)
        for k, v in self.buckets[idx]:
            if k == key:
                return v
        return None
```

## The Gotcha
Hash collisions! Two keys can hash to same index. Good hash functions minimize this, but you MUST handle it (chaining or probing).

## Real-World Example
Database indexes, Redis caches, symbol tables, deduplication in security logs (seen this IP before?).

## Micro Challenge
Why does Python's dict guarantee insertion order since 3.7, but hash maps traditionally don't?

---

**Related**: []  
**Next**: [Consistent Hashing]
