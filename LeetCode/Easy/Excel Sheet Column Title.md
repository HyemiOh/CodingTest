# Excel Sheet Column Title

[LeetCode - Excel Sheet Column Title](https://leetcode.com/problems/excel-sheet-column-title/)

### Description

Given an integer `columnNumber`, return *its corresponding column title as it appears in an Excel sheet*.

For example:

```
A -> 1
B -> 2
C -> 3
...
Z -> 26
AA -> 27
AB -> 28
...
```

**Example 1:**

```
Input: columnNumber = 1
Output: "A"
```

**Example 2:**

```
Input: columnNumber = 28
Output: "AB"
```

**Example 3:**

```
Input: columnNumber = 701
Output: "ZY"
```

**Constraints:**

- `1 <= columnNumber <= 231 - 1`

### Solution

```kotlin
class Solution {
    fun convertToTitle(columnNumber: Int): String {
        var answer = ""
        var number = columnNumber

        while (number > 0) {
            answer = ((number - 1) % 26 + 'A'.toInt()).toChar() + answer
            number = (number - 1) / 26
        }
        return answer
    }
}
```