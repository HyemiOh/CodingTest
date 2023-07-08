# Search in a Binary Search Tree

[Search in a Binary Search Tree - LeetCode](https://leetcode.com/problems/search-in-a-binary-search-tree/description/?envType=study-plan-v2&envId=leetcode-75)

### Description

You are given the `root` of a binary search tree (BST) and an integer `val`.

Find the node in the BST that the node's value equals `val` and return the subtree rooted with that node. If such a node does not exist, return `null`.

**Example 1:**

!https://assets.leetcode.com/uploads/2021/01/12/tree1.jpg

```
Input: root = [4,2,7,1,3], val = 2
Output: [2,1,3]
```

**Example 2:**

!https://assets.leetcode.com/uploads/2021/01/12/tree2.jpg

```
Input: root = [4,2,7,1,3], val = 5
Output: []
```

**Constraints:**

- The number of nodes in the tree is in the range `[1, 5000]`.
- `1 <= Node.val <= 107`
- `root` is a binary search tree.
- `1 <= val <= 107`

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
    fun searchBST(root: TreeNode?, `val`: Int): TreeNode? {
        if(root == null) return root
        
        if(root.`val` > `val`)
            return searchBST(root.left, `val`)
        else if(root.`val` < `val`)
            return searchBST(root.right, `val`)
        else return root
    }
}
```