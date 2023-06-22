# Count Good Nodes in Binary Tree

[Count Good Nodes in Binary Tree - LeetCode](https://leetcode.com/problems/count-good-nodes-in-binary-tree/description/?envType=study-plan-v2&envId=leetcode-75)

### Description

Given a binary tree `root`, a node *X* in the tree is named **good** if in the path from root to *X* there are no nodes with a value *greater than* X.

Return the number of **good** nodes in the binary tree.

**Example 1:**

```
Input: root = [3,1,4,3,null,1,5]
Output: 4
Explanation: Nodes in blue aregood.
Root Node (3) is always a good node.
Node 4 -> (3,4) is the maximum value in the path starting from the root.
Node 5 -> (3,4,5) is the maximum value in the path
Node 3 -> (3,1,3) is the maximum value in the path.
```

**Example 2:**

```
Input: root = [3,3,null,4,2]
Output: 3
Explanation: Node 2 -> (3, 3, 2) is not good, because "3" is higher than it.
```

**Example 3:**

```
Input: root = [1]
Output: 1
Explanation: Root is considered asgood.
```

**Constraints:**

- The number of nodes in the binary tree is in the range `[1, 10^5]`.
- Each node's value is between `[-10^4, 10^4]`.

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
    var count = 0

    fun goodNodes(root: TreeNode?): Int {
				if(root == null) return 0

        isMaxNode(root, root.`val`)

        return count
    }

    fun isMaxNode(root: TreeNode?, maxNum: Int) {
        if(root == null) return

        if(root.`val` >= maxNum) {
            count++
        }

        val max = Math.max(root.`val`, maxNum)
        isMaxNode(root.left, max)
        isMaxNode(root.right, max)
    }
}
```