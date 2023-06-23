# Deepest Leaves Sum

[Deepest Leaves Sum - LeetCode](https://leetcode.com/problems/deepest-leaves-sum/description/)

### Descrition

Given the `root` of a binary tree, return *the sum of values of its deepest leaves*.

**Example 1:**

```
Input: root = [1,2,3,4,5,null,6,7,null,null,null,null,8]
Output: 15
```

**Example 2:**

```
Input: root = [6,7,8,2,7,1,3,9,null,1,4,null,null,null,5]
Output: 19
```

**Constraints:**

- The number of nodes in the tree is in the range `[1, 104]`.
- `1 <= Node.val <= 100`

### Solution

```kotlin
/**
 * Example:
 * var ti = TreeNode(5)
 * var v = ti.`val`
 * Definition for a binary tree node.
 * class TreeNode(var `val`: Int) {
 *     var left: TreeNode? = null
 *     var right: TreeNode? = null
 * }
 */
class Solution {
    val answer = hashMapOf<Int, Int>()

    fun deepestLeavesSum(root: TreeNode?): Int {
        if(root == null) return 0

        answer[0] = root?.`val`
        deepestLeave(root, 0)

        return answer[answer.keys.max()?.minus(1)] ?: root.`val`
    }

    fun deepestLeave(root: TreeNode?, maxDeep: Int) {
        if(root == null) return

        answer[maxDeep + 1] = (answer[maxDeep + 1] ?: 0) +(root.left?.`val` ?: 0) + (root.right?.`val` ?: 0)
        
        deepestLeave(root.left, maxDeep + 1)
        deepestLeave(root.right, maxDeep + 1)
    }
}
```