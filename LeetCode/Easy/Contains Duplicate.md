# Contains Duplicate

[Contains Duplicate - LeetCode](https://leetcode.com/problems/contains-duplicate/description/)

### 문제 설명

Given an integer array `nums`, return `true` if any value appears **at least twice** in the array, and return `false` if every element is distinct.

**Example 1:**

```
Input: nums = [1,2,3,1]
Output: true

```

**Example 2:**

```
Input: nums = [1,2,3,4]
Output: false

```

**Example 3:**

```
Input: nums = [1,1,1,3,3,4,3,2,4,2]
Output: true

```

**Constraints:**

- `1 <= nums.length <= 105`
- `109 <= nums[i] <= 109`

### 나의 풀이

```kotlin
class Solution {
    fun containsDuplicate(nums: IntArray): Boolean {
        return nums.groupBy{ it }.size != nums.size
    }
}
```

- nums에서 중복된 수가 있으면 true, 모두 고유하면 false를 리턴