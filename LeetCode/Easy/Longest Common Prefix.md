# Longest Common Prefix

[Longest Common Prefix - LeetCode](https://leetcode.com/problems/longest-common-prefix/description/)

### 문제 설명

Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string `""`.

**Example 1:**

```
Input: strs = ["flower","flow","flight"]
Output: "fl"
```

**Example 2:**

```
Input: strs = ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.
```

**Constraints:**

- `1 <= strs.length <= 200`
- `0 <= strs[i].length <= 200`
- `strs[i]` consists of only lowercase English letters.

### 나의 풀이

```kotlin
class Solution {
    fun longestCommonPrefix(strs: Array<String>): String {
        var answer = ""
        val first = strs.first()

        for(i in 1 .. first.length) {
            val subString = first.take(i)
            if(strs.count { it.take(i) == subString } == strs.size)
                answer = subString
        }

        return answer
    }
}
```