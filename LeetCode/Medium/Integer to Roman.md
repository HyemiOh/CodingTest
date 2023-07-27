# Integer to Roman

[LeetCode - Integer to Roman](https://leetcode.com/problems/integer-to-roman/description/?envType=study-plan-v2&envId=top-interview-150)

### Description

Roman numerals are represented by seven different symbols: `I`, `V`, `X`, `L`, `C`, `D` and `M`.

```
SymbolValue
I             1
V             5
X             10
L             50
C             100
D             500
M             1000
```

For example, `2` is written as `II` in Roman numeral, just two one's added together. `12` is written as `XII`, which is simply `X + II`. The number `27` is written as `XXVII`, which is `XX + V + II`.

Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not `IIII`. Instead, the number four is written as `IV`. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as `IX`. There are six instances where subtraction is used:

- `I` can be placed before `V` (5) and `X` (10) to make 4 and 9.
- `X` can be placed before `L` (50) and `C` (100) to make 40 and 90.
- `C` can be placed before `D` (500) and `M` (1000) to make 400 and 900.

Given an integer, convert it to a roman numeral.

**Example 1:**

```
Input: num = 3
Output: "III"
Explanation: 3 is represented as 3 ones.
```

**Example 2:**

```
Input: num = 58
Output: "LVIII"
Explanation: L = 50, V = 5, III = 3.
```

**Example 3:**

```
Input: num = 1994
Output: "MCMXCIV"
Explanation: M = 1000, CM = 900, XC = 90 and IV = 4.
```

**Constraints:**

- `1 <= num <= 3999`

### Solution

```kotlin
class Solution {
    fun intToRoman(num: Int): String {
        var answer = ""
        val map = mapOf(
            1 to "I",
            5 to "V",
            10 to "X",
            50 to "L",
            100 to "C",
            500 to "D",
            1000 to "M"
        )

        var number = num
        var div = 10

        while(div <= 10000) {
            val rest = number % div
            if(rest != 0) {
                val pow = div / 10
                answer = if(map.containsKey(rest)) {
                    map.getOrDefault(rest, "")
                }
                else {
                    when(rest / pow) {
                        4 -> {
                            map.getOrDefault(1 * pow, "") + map.getOrDefault(5 * pow, "")
                        }

                        9 -> {
                            map.getOrDefault(1 * pow, "") + map.getOrDefault(1 * pow * 10, "")
                        }

                        else -> {
                            val division = rest / pow / 5
                            val re = rest / pow % 5
                            var add = if(division == 1) map.getOrDefault(5 * pow, "") else ""
                            repeat(re) {
                                add += map.getOrDefault(1 * pow, "")
                            }
                            add
                        }

                    }
                } + answer
            }

            number -= rest
            div *= 10
        }

        return answer
    }
}
```