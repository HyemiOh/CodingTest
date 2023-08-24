# Longest Substring Without Repeating Characters

[LeetCode - Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/?envType=study-plan-v2&envId=top-interview-150)

### Description

Given a string `s`, find the length of the **longest**

**substring**

without repeating characters.

**Example 1:**

```
Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.
```

**Example 2:**

```
Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```

**Example 3:**

```
Input: s = "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3.
Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.
```

**Constraints:**

- `0 <= s.length <= 5 * 104`
- `s` consists of English letters, digits, symbols and spaces.

### Solution

```kotlin
class Solution {
    fun lengthOfLongestSubstring(s: String): Int {
        val list = mutableListOf<Char>()
        var max = 1
        var index = 0

        s.forEach {
            if(it !in list) {
                list.add(it)
                max = Math.max(list.size, max)
            }
            else {
                index = list.indexOf(it)
                list.add(it)
                while (index >= 0) {
                    list.removeAt(index)
                    index--
                }
            }
        }
        return max
    }
}
```