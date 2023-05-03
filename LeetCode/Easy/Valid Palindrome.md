# Valid Palindrome

[Valid Palindrome - LeetCode](https://leetcode.com/problems/valid-palindrome/description/)

### 문제 설명

A phrase is a **palindrome** if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.

Given a string `s`, return `true` *if it is a **palindrome**, or* `false` *otherwise*.

**Example 1:**

```
Input: s = "A man, a plan, a canal: Panama"
Output: true
Explanation: "amanaplanacanalpanama" is a palindrome.

```

**Example 2:**

```
Input: s = "race a car"
Output: false
Explanation: "raceacar" is not a palindrome.

```

**Example 3:**

```
Input: s = " "
Output: true
Explanation: s is an empty string "" after removing non-alphanumeric characters.
Since an empty string reads the same forward and backward, it is a palindrome.

```

**Constraints:**

- `1 <= s.length <= 2 * 105`
- `s` consists only of printable ASCII characters.

### 나의 풀이

```kotlin
class Solution {
    fun isPalindrome(s: String): Boolean {
        val list = s.toLowerCase().filter { it.isLetterOrDigit() }
        return list == list.reversed()
    }
}
```

- 모든 대문자를 소문자로 변환하고 영문자와 숫자가 아닌 문자는 제외한 후 앞뒤로 똑같은 스트링을 찾는 문제.