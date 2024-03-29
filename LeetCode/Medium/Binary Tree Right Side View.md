# Binary Tree Right Side View

[Binary Tree Right Side View - LeetCode](https://leetcode.com/problems/binary-tree-right-side-view/description/?envType=study-plan-v2&envId=leetcode-75)

### Description

Given the `root` of a binary tree, imagine yourself standing on the **right side** of it, return *the values of the nodes you can see ordered from top to bottom*.

**Example 1:**

!https://assets.leetcode.com/uploads/2021/02/14/tree.jpg

```
Input: root = [1,2,3,null,5,null,4]
Output: [1,3,4]
```

**Example 2:**

```
Input: root = [1,null,3]
Output: [1,3]
```

**Example 3:**

```
Input: root = []
Output: []
```

**Constraints:**

- The number of nodes in the tree is in the range `[0, 100]`.
- `100 <= Node.val <= 100`

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
    fun rightSideView(root: TreeNode?): List<Int> {
        val answer = mutableListOf<Int>()
        getRightSide(root, 0, answer)

        return answer
    }

    fun getRightSide(root: TreeNode?, depth: Int, answer: MutableList<Int>) {
        if(root == null) return

        if(depth == answer.size) {
            answer.add(root.`val`)
        }

        getRightSide(root.right, depth + 1, answer)
        getRightSide(root.left, depth + 1, answer)
    }
}
```