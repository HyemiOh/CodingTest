# 3Sum

[LeetCode - 3Sum](https://leetcode.com/problems/3sum/description/?envType=study-plan-v2&envId=top-interview-150)

### Description

Given an integer array nums, return all the triplets `[nums[i], nums[j], nums[k]]` such that `i != j`, `i != k`, and `j != k`, and `nums[i] + nums[j] + nums[k] == 0`.

Notice that the solution set must not contain duplicate triplets.

**Example 1:**

```
Input: nums = [-1,0,1,2,-1,-4]
Output: [[-1,-1,2],[-1,0,1]]
Explanation:
nums[0] + nums[1] + nums[2] = (-1) + 0 + 1 = 0.
nums[1] + nums[2] + nums[4] = 0 + 1 + (-1) = 0.
nums[0] + nums[3] + nums[4] = (-1) + 2 + (-1) = 0.
The distinct triplets are [-1,0,1] and [-1,-1,2].
Notice that the order of the output and the order of the triplets does not matter.
```

**Example 2:**

```
Input: nums = [0,1,1]
Output: []
Explanation: The only possible triplet does not sum up to 0.
```

**Example 3:**

```
Input: nums = [0,0,0]
Output: [[0,0,0]]
Explanation: The only possible triplet sums up to 0.
```

**Constraints:**

- `3 <= nums.length <= 3000`
- `105 <= nums[i] <= 105`

### Solution

```java
class Solution {
    fun threeSum(nums: IntArray): List<List<Int>> {
        val answer = mutableSetOf<List<Int>>()
        nums.sort()

        for(i in 0..nums.lastIndex - 2) {
            var start = i + 1
            var end = nums.lastIndex

            while (start < end) {
                val sum = nums[i] + nums[start] + nums[end]
                when {
                    sum == 0 -> {
                        answer.add(listOf(nums[i], nums[start], nums[end]))
                        start++
                        end--
                    }
                    sum < 0 -> start++
                    else -> end--
                }
            }
        }

        return answer.toList()
    }
}
```