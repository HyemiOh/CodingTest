# Maximum Number of Vowels in a Substring of Given Length

[Maximum Number of Vowels in a Substring of Given Length - LeetCode](https://leetcode.com/problems/maximum-number-of-vowels-in-a-substring-of-given-length/description/?envType=study-plan-v2&envId=leetcode-75)

### Description

Given a string `s` and an integer `k`, return *the maximum number of vowel letters in any substring of* `s` *with length* `k`.

**Vowel letters** in English are `'a'`, `'e'`, `'i'`, `'o'`, and `'u'`.

**Example 1:**

```
Input: s = "abciiidef", k = 3
Output: 3
Explanation: The substring "iii" contains 3 vowel letters.
```

**Example 2:**

```
Input: s = "aeiou", k = 2
Output: 2
Explanation: Any substring of length 2 contains 2 vowels.
```

**Example 3:**

```
Input: s = "leetcode", k = 3
Output: 2
Explanation: "lee", "eet" and "ode" contain 2 vowels.
```

**Constraints:**

- `1 <= s.length <= 105`
- `s` consists of lowercase English letters.
- `1 <= k <= s.length`

### Solution

```kotlin
class Solution {
    fun maxVowels(s: String, k: Int): Int {
        var answer = 0
        val vowel = charArrayOf('a', 'e', 'i', 'o', 'u')

        for(i in 0 until k) {
            if(vowel.contains(s[i]))
                answer++
        }

        var newAnswer = answer
        for(i in k until s.length) {
            if(vowel.contains(s[i - k])) newAnswer--
            if(vowel.contains(s[i])) newAnswer++
            answer = kotlin.math.max(answer, newAnswer)
        }

        return answer
    }
}
```