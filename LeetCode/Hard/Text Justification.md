# Text Justification

[LeetCode - Text Justification](https://leetcode.com/problems/text-justification/)

### Description

Given an array of strings `words` and a width `maxWidth`, format the text such that each line has exactly `maxWidth` characters and is fully (left and right) justified.

You should pack your words in a greedy approach; that is, pack as many words as you can in each line. Pad extra spaces `' '` when necessary so that each line has exactly `maxWidth` characters.

Extra spaces between words should be distributed as evenly as possible. If the number of spaces on a line does not divide evenly between words, the empty slots on the left will be assigned more spaces than the slots on the right.

For the last line of text, it should be left-justified, and no extra space is inserted between words.

**Note:**

- A word is defined as a character sequence consisting of non-space characters only.
- Each word's length is guaranteed to be greater than `0` and not exceed `maxWidth`.
- The input array `words` contains at least one word.

**Example 1:**

```
Input: words = ["This", "is", "an", "example", "of", "text", "justification."], maxWidth = 16
Output:
[
   "This    is    an",
   "example  of text",
   "justification.  "
]
```

**Example 2:**

```
Input: words = ["What","must","be","acknowledgment","shall","be"], maxWidth = 16
Output:
[
  "What   must   be",
  "acknowledgment  ",
  "shall be        "
]
Explanation: Note that the last line is "shall be    " instead of "shall     be", because the last line must be left-justified instead of fully-justified.
Note that the second line is also left-justified because it contains only one word.
```

**Example 3:**

```
Input: words = ["Science","is","what","we","understand","well","enough","to","explain","to","a","computer.","Art","is","everything","else","we","do"], maxWidth = 20
Output:
[
  "Science  is  what we",
  "understand      well",
  "enough to explain to",
  "a  computer.  Art is",
  "everything  else  we",
  "do                  "
]
```

**Constraints:**

- `1 <= words.length <= 300`
- `1 <= words[i].length <= 20`
- `words[i]` consists of only English letters and symbols.
- `1 <= maxWidth <= 100`
- `words[i].length <= maxWidth`

### Solution

```java
class Solution {
    fun fullJustify(words: Array<String>, maxWidth: Int): List<String> {
        val formatList = mutableListOf<String>()
        val formatMap = mutableMapOf<Int, MutableList<String>>()

        var num = 0
        words.forEachIndexed { index, word ->
            if(formatMap.isEmpty()) {
                num++
                formatMap[num] = mutableListOf(word)
            }
            else {
                val last = formatMap.getOrDefault(num, mutableListOf())
                val lastLength = last.map { it.length }.sum()
                if(lastLength + last.size + word.length > maxWidth) {
                    num++
                    formatMap[num] = mutableListOf(word)

                    val list = formatMap.getOrDefault(num - 1, mutableListOf())
                    val length = last.map { it.length }.sum()
                    if(list.size == 1) {
                        formatList.add(list.joinToString() + " ".repeat(maxWidth - list.first().length))
                    }
                    else {
                        val div = (maxWidth - length) / list.lastIndex
                        var remain = (maxWidth - length) % list.lastIndex
                        var join = ""
                        list.forEachIndexed { index, s ->
                            if(index == list.lastIndex) {
                                join += s
                            }
                            else {
                                join += s + " ".repeat(div)
                                if(remain != 0) {
                                    join += " "
                                    remain--
                                }
                            }
                        }
                        formatList.add(join)
                    }
                }
                else {
                    formatMap.getOrDefault(num, mutableListOf()).add(word)
                }
            }
        }

        val list = formatMap.getOrDefault(num, mutableListOf())
        val join = list.joinToString(" ")
        formatList.add(join + " ".repeat(maxWidth - join.length))

        return formatList
    }
}
```

- words를 한 줄로 출력 되어야 하는 단어 별로 map에 set 해주었다.
- map 마지막 인덱스의 리스트 모든 word의 길이 + 리스트 사이즈 + 현재 word 가 maxWidth보다 클 때는 다음 줄에 추가 되어야 하기 때문에 map에 추가해주고 마감된 리스트는 조건에 맞춰 공백을 추가한 문자열로 만들어 리턴할 리스트에 추가해주었다.
- 공백의 개수는 (maxWidth - 리스트 모든 word길이)에 리스트 길이 - 1 을 나눈 몫과 나머지는 빠른 인덱스부터 한개씩 나눠가졌다
- 마지막 map은 조건이 다르므로 단어 사이에 공백 하나씩만 두고 오른쪽에 나머지 공백을 넣어주었다.