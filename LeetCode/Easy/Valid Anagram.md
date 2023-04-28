# Valid Anagram

[Valid Anagram - LeetCode](https://leetcode.com/problems/valid-anagram/)

### 문제 설명

Given two strings `s` and `t`, return `true` *if* `t` *is an anagram of* `s`*, and* `false` *otherwise*.

An **Anagram** is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

**Example 1:**

```
Input: s = "anagram", t = "nagaram"
Output: true
```

**Example 2:**

```
Input: s = "rat", t = "car"
Output: false
```

**Constraints:**

- `1 <= s.length, t.length <= 5 * 104`
- `s` and `t` consist of lowercase English letters.

### 나의 풀이

```kotlin
class Solution {
    fun isAnagram(s: String, t: String): Boolean {
        return s.toList().sorted() == t.toList().sorted()
    }
}
```