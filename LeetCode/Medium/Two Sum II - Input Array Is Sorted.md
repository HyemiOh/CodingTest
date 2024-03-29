# Two Sum II - Input Array Is Sorted

[Two Sum II - Input Array Is Sorted - LeetCode](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/)

### 문제 설명

Given a **1-indexed** array of integers `numbers` that is already ***sorted in non-decreasing order***, find two numbers such that they add up to a specific `target` number. Let these two numbers be `numbers[index1]` and `numbers[index2]` where `1 <= index1 < index2 <= numbers.length`.

Return *the indices of the two numbers,* `index1` *and* `index2`*, **added by one** as an integer array* `[index1, index2]` *of length 2.*

The tests are generated such that there is **exactly one solution**. You **may not** use the same element twice.

Your solution must use only constant extra space.

**Example 1:**

```
Input: numbers = [2,7,11,15], target = 9
Output: [1,2]
Explanation: The sum of 2 and 7 is 9. Therefore, index1 = 1, index2 = 2. We return [1, 2].

```

**Example 2:**

```
Input: numbers = [2,3,4], target = 6
Output: [1,3]
Explanation: The sum of 2 and 4 is 6. Therefore index1 = 1, index2 = 3. We return [1, 3].

```

**Example 3:**

```
Input: numbers = [-1,0], target = -1
Output: [1,2]
Explanation: The sum of -1 and 0 is -1. Therefore index1 = 1, index2 = 2. We return [1, 2].

```

**Constraints:**

- `2 <= numbers.length <= 3 * 104`
- `1000 <= numbers[i] <= 1000`
- `numbers` is sorted in **non-decreasing order**.
- `1000 <= target <= 1000`
- The tests are generated such that there is **exactly one solution**.

### 나의 풀이

```kotlin
class Solution {
    fun twoSum(numbers: IntArray, target: Int): IntArray {
        val answer = IntArray(2)
        for(i in 0 until numbers.lastIndex) {
            for(j in (i + 1) .. numbers.lastIndex) {
                if(numbers[i] + numbers[j] == target) {
                    answer[0] = i + 1
                    answer[1] = j + 1
                    break
                }
            }
        }
        return answer
    }
}
```

- 리스트에서 두 원소를 더했을때 target과 같으면 해당 원소의 인덱스 + 1을 반환하는 문제이다.

```kotlin
class Solution {
    fun twoSum(numbers: IntArray, target: Int): IntArray {
        var i = 1
        var j = numbers.size

        while(true) {
            val sum = numbers[i - 1] + numbers[j - 1]
            when {
                sum == target -> break
                sum > target -> j--
                else -> i++
            }
        }
        return intArrayOf(i, j)
    }
}
```

- 시간복잡도 O(n)으로 다시 풀어보았다