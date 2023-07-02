# Maximum Depth of Binary Tree

[LeetCode - The World's Leading Online Programming Learning Platform](https://leetcode.com/problems/maximum-depth-of-binary-tree/submissions/976883194/?envType=study-plan-v2&envId=leetcode-75)

### Description

Given the `root` of a binary tree, return *its maximum depth*.

A binary tree's **maximum depth** is the number of nodes along the longest path from the root node down to the farthest leaf node.

**Example 1:**

```
Input: root = [3,9,20,null,null,15,7]
Output: 3
```

**Example 2:**

```
Input: root = [1,null,2]
Output: 2
```

**Constraints:**

- The number of nodes in the tree is in the range `[0, 104]`.
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
    fun maxDepth(root: TreeNode?): Int {
        var answer = 0
        val stack = Stack<Pair<TreeNode?, Int>>()
        stack.add(Pair(root, 1))

        while(stack.isNotEmpty()) {
            val node = stack.pop()
            node.first?.let {
                answer = Math.max(answer, node.second)
                stack.add(Pair(it.left, node.second + 1))
                stack.add(Pair(it.right, node.second + 1))
            }
        }

        return answer
    }
}
```