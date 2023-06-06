# Reverse Vowels of a String

[Reverse Vowels of a String - LeetCode](https://leetcode.com/problems/reverse-vowels-of-a-string/description/?envType=study-plan-v2&envId=leetcode-75)

### Description

Given a string `s`, reverse only all the vowels in the string and return it.

The vowels are `'a'`, `'e'`, `'i'`, `'o'`, and `'u'`, and they can appear in both lower and upper cases, more than once.

**Example 1:**

```
Input: s = "hello"
Output: "holle"
```

**Example 2:**

```
Input: s = "leetcode"
Output: "leotcede"
```

**Constraints:**

- `1 <= s.length <= 3 * 105`
- `s` consist of **printable ASCII** characters.

### Solution

```kotlin
class Solution {
    fun reverseVowels(s: String): String {
        val vowels = listOf('a', 'e', 'i', 'o', 'u')
        val vowelList = s.filter { it.toLowerCase() in vowels }.reversed()
        val stringList = s.toMutableList()
        var num = 0
        for(i in stringList.indices) {
            if(stringList[i].toLowerCase() in vowels) {
                stringList[i] = vowelList[num]
                num++
            }
        }

        return stringList.joinToString("")
    }
}
```