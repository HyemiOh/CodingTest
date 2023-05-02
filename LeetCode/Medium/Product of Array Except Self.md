# Product of Array Except Self

[Product of Array Except Self - LeetCode](https://leetcode.com/problems/product-of-array-except-self/description/)

### 문제 설명

Given an integer array `nums`, return *an array* `answer` *such that* `answer[i]` *is equal to the product of all the elements of* `nums` *except* `nums[i]`.

The product of any prefix or suffix of `nums` is **guaranteed** to fit in a **32-bit** integer.

You must write an algorithm that runs in `O(n)` time and without using the division operation.

**Example 1:**

```
Input: nums = [1,2,3,4]
Output: [24,12,8,6]

```

**Example 2:**

```
Input: nums = [-1,1,0,-3,3]
Output: [0,0,9,0,0]

```

**Constraints:**

- `2 <= nums.length <= 105`
- `30 <= nums[i] <= 30`
- The product of any prefix or suffix of `nums` is **guaranteed** to fit in a **32-bit** integer.

**Follow up:** Can you solve the problem in `O(1)` extra space complexity? (The output array **does not** count as extra space for space complexity analysis.)

### 나의 풀이

```kotlin
class Solution {
    fun productExceptSelf(nums: IntArray): IntArray {
        val answer = IntArray(nums.size)
        var num = 1
        for(i in 0..nums.lastIndex)
        {
            answer[i] = num
            num *= nums[i]
        }
        num = 1
        for(i in nums.lastIndex downTo 0)
        {
            answer[i] = num * answer[i]
            num *= nums[i]
        }

        return answer
    }
}
```
- 현재 인덱스보다 앞에 있는 원소들과 뒤에있는 원소들의 곱을 구하는 문제
- 시간복잡도를 O(N)으로 풀어야하기 때문에 먼저 앞에 있는 원소들의 곱을 구한 후 뒤에 있는 원소들의 곱을 구해 곱해줬다