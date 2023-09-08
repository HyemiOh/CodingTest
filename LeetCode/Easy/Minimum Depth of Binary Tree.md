# Minimum Depth of Binary Tree

[LeetCode - Minimum Depth of Binary Tree](https://leetcode.com/problems/minimum-depth-of-binary-tree/description/)

### Description

Given a binary tree, find its minimum depth.

The minimum depth is the number of nodes along the shortest path from the root node down to the nearest leaf node.

**Note:** A leaf is a node with no children.

**Example 1:**

![https://assets.leetcode.com/uploads/2020/10/12/ex_depth.jpg](https://assets.leetcode.com/uploads/2020/10/12/ex_depth.jpg)

```
Input: root = [3,9,20,null,null,15,7]
Output: 2
```

**Example 2:**

```
Input: root = [2,null,3,null,4,null,5,null,6]
Output: 5
```

**Constraints:**

- The number of nodes in the tree is in the range `[0, 105]`.
- `1000 <= Node.val <= 1000`

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
    var answer = Int.MAX_VALUE

    fun minDepth(root: TreeNode?): Int {
        if(root == null) return 0
        depth(root, 1)

        return answer
    }

    fun depth(root: TreeNode?, level: Int) {
        root?.let {
            if(it.left == null && it.right == null) {
                answer = Math.min(level, answer)
            }
            else {    
                depth(it.left, level + 1)
                depth(it.right, level + 1)
            }
        } 
    }
}
```