# Max Consecutive Ones III

[Max Consecutive Ones III - LeetCode](https://leetcode.com/problems/max-consecutive-ones-iii/description/?envType=study-plan-v2&envId=leetcode-75)

### Description

Given a binary array `nums` and an integer `k`, return *the maximum number of consecutive* `1`*'s in the array if you can flip at most* `k` `0`'s.

**Example 1:**

```
Input: nums = [1,1,1,0,0,0,1,1,1,1,0], k = 2
Output: 6
Explanation: [1,1,1,0,0,1,1,1,1,1,1]
Bolded numbers were flipped from 0 to 1. The longest subarray is underlined.
```

**Example 2:**

```
Input: nums = [0,0,1,1,0,0,1,1,1,0,1,1,0,0,0,1,1,1,1], k = 3
Output: 10
Explanation: [0,0,1,1,1,1,1,1,1,1,1,1,0,0,0,1,1,1,1]
Bolded numbers were flipped from 0 to 1. The longest subarray is underlined.
```

**Constraints:**

- `1 <= nums.length <= 105`
- `nums[i]` is either `0` or `1`.
- `0 <= k <= nums.length`

### Solution

```kotlin
class Solution {
    fun longestOnes(nums: IntArray, k: Int): Int {
        var answer = 0
        var zero = 0
        var start = 0
        nums.forEachIndexed { index, num ->
            if(num == 0) {
                zero++
            }
            if(zero > k) {
                if(nums[start] == 0)
                    zero--
                start++
            }
            answer = kotlin.math.max(answer, index - start + 1)
        }

        return answer
    }
}
```