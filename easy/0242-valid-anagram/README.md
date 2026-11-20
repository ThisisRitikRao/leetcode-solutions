# Valid Anagram

![Difficulty](https://img.shields.io/badge/Difficulty-Easy-green)

## Problem

Given two strings `s` and `t`, return `true` if `t` is an anagram of `s`, and `false` otherwise.

 

Original
Java
**Example 1:**

**Input:** s = "anagram", t = "nagaram"

**Output:** true

**Example 2:**

**Input:** s = "rat", t = "car"

**Output:** false

 

**Constraints:**

- 1 <= s.length, t.length <= 5 * 104
- s and t consist of lowercase English letters.

 

**Follow up:** What if the inputs contain Unicode characters? How would you adapt your solution to such a case?

## Solution

**Language:** Java  
**Runtime:** 21 ms (beats 8.87%)  
**Memory:** 46.3 MB (beats 28.71%)  
**Submitted:** 2026-11-20T14:04:25.250Z  

```java
class Solution {
    public boolean isAnagram(String s, String t) {
        if(s.length() != t.length()){
            return false;
        }
        HashMap<Character, Integer> map = new HashMap<>();
        for(int i = 0; i < s.length(); i++){
            map.put(s.charAt(i), map.getOrDefault(s.charAt(i), 0) + 1);
        }
        for(char ch: t.toCharArray()){
            if(!map.containsKey(ch)) return false;
            map.put(ch, map.get(ch)-1);
            if(map.get(ch) == 0) map.remove(ch);
        }
        return map.isEmpty();
    }
}
```

---

[View on LeetCode](https://leetcode.com/problems/valid-anagram/)