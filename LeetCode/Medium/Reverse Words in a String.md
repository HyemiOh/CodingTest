# Reverse Words in a String

[Reverse Words in a String - LeetCode](https://leetcode.com/problems/reverse-words-in-a-string/description/?envType=study-plan-v2&id=leetcode-75)

### Description

Given an input string `s`, reverse the order of the **words**.

A **word** is defined as a sequence of non-space characters. The **words** in `s` will be separated by at least one space.

Return *a string of the words in reverse order concatenated by a single space.*

**Note** that `s` may contain leading or trailing spaces or multiple spaces between two words. The returned string should only have a single space separating the words. Do not include any extra spaces.

**Example 1:**

```
Input: s = "the sky is blue"
Output: "blue is sky the"

```

**Example 2:**

```
Input: s = "  hello world  "
Output: "world hello"
Explanation: Your reversed string should not contain leading or trailing spaces.

```

**Example 3:**

```
Input: s = "a good   example"
Output: "example good a"
Explanation: You need to reduce multiple spaces between two words to a single space in the reversed string.

```

**Constraints:**

- `1 <= s.length <= 104`
- `s` contains English letters (upper-case and lower-case), digits, and spaces `' '`.
- There is **at least one** word in `s`.

### Solution

```kotlin
class Solution {
    fun reverseWords(s: String): String {
        var answer = ""
        val splitList = s.split(" ").reversed().filter { it.isNotEmpty() }

        splitList.forEachIndexed { index, word ->
            answer += word
            if(index != splitList.lastIndex) answer += " "
        }
        return answer
    }
}
```