# Single Element in a Sorted Array

[Single Element in a Sorted Array - LeetCode](https://leetcode.com/problems/single-element-in-a-sorted-array/description/)

### 문제 설명

You are given a sorted array consisting of only integers where every element appears exactly twice, except for one element which appears exactly once.

Return *the single element that appears only once*.

Your solution must run in `O(log n)` time and `O(1)` space.

**Example 1:**

```
Input: nums = [1,1,2,3,3,4,4,8,8]
Output: 2

```

**Example 2:**

```
Input: nums = [3,3,7,7,10,11,11]
Output: 10

```

**Constraints:**

- `1 <= nums.length <= 105`
- `0 <= nums[i] <= 105`

### 나의 풀이

```kotlin
class Solution {
    fun singleNonDuplicate(nums: IntArray): Int {
        var answer = 0
        while(answer < nums.lastIndex) {
            if(nums[answer] != nums[answer + 1]) return nums[answer]
            answer += 2
        }
        return nums.last()
    }
}
```