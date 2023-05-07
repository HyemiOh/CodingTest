# Valid Parentheses

[Valid Parentheses - LeetCode](https://leetcode.com/problems/valid-parentheses/description/)

### 문제 설명

Given a string `s` containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

An input string is valid if:

1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.
3. Every close bracket has a corresponding open bracket of the same type.

**Example 1:**

```
Input: s = "()"
Output: true
```

**Example 2:**

```
Input: s = "()[]{}"
Output: true
```

**Example 3:**

```
Input: s = "(]"
Output: false
```

**Constraints:**

- `1 <= s.length <= 104`
- `s` consists of parentheses only `'()[]{}'`.

### 나의 풀이

```kotlin
class Solution {
    fun isValid(s: String): Boolean {
        val answer = Stack<Char>()
        s.forEach {
            when(it) {
                ')' -> {
                    if(answer.isNotEmpty() && answer.peek() == '(')
                        answer.pop()
                    else return false
                }
                '}' -> {
                    if(answer.isNotEmpty() && answer.peek() == '{')
                        answer.pop()
                    else return false
                }
                ']' -> {
                    if(answer.isNotEmpty() && answer.peek() == '[')
                        answer.pop()
                    else return false
                }
                else -> {
                    answer.push(it)
                }
            }
        }
        return answer.isEmpty()
    }
}
```