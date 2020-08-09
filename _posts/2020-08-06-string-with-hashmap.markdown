---
layout: post
title:  "String with HashMaps"
date:   2020-08-06 12:30:00 +0700
categories: Py Competitive-Programming
---

String with HashMaps.

**1. checkPalindrome**

```py
# Basic
def isPalindrome(s):
    return s == s[::-1]

s1 = "rotator"
s2 = "level"

print(isPalindrome(s1)) # True
print(isPalindrome(s2)) # True
```

**2. checkAnagram**
```py
# Basic - Time Complexity: O(nlogn)
def isAnagram(s1, s2):
    return sorted(s1) == sorted(s2)

s1 = "SILENT"
s2 = "LISTEN"

print(isAnagram(s1, s2)) # True
```
```py
# Time Complexity: O(n)
from collections import Counter
def isAnagram(s1, s2):
    return Counter(s1) == Counter(s2)
```
**3. Sort by len**
```py
s = "Hello world welcome to programming Happy Coding"
A = s.split()
A.sort(key=len,reverse=True)
print(A)
# Output: ['programming', 'welcome', 'Coding', 'Hello', 'world', 'Happy', 'to']
```
**4. Sort by Frequency**
```py
s = "programmingknowledge"
from collections import Counter
CT = Counter(s)
print(CT)
# Output: Counter({'g': 3, 'r': 2, 'o': 2, 'm': 2, 'n': 2, 'e': 2, 'p': 1, 'a': 1, 'i': 1, 'k': 1, 'w': 1, 'l': 1, 'd': 1})
A = list(CT.items())
A.sort(key=lambda x:[x[1], x[0]])
print(A)
# Output: [('a', 1), ('d', 1), ('i', 1), ('k', 1), ('l', 1), ('p', 1), ('w', 1), ('e', 2), ('m', 2), ('n', 2), ('o', 2), ('r', 2), ('g', 3)]
```

{% gist df568f2c23a3854719f7ac539e4d1aa2 %}