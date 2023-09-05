# Linked List Cycle

[LeetCode - Linked List Cycle
](https://leetcode.com/problems/linked-list-cycle/description/?envType=daily-question&envId=2023-09-04)

### Description

Given `head`, the head of a linked list, determine if the linked list has a cycle in it.

There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the `next` pointer. Internally, `pos` is used to denote the index of the node that tail's `next` pointer is connected to. **Note that `pos` is not passed as a parameter**.

Return `true` *if there is a cycle in the linked list*. Otherwise, return `false`.

**Example 1:**

![https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist.png](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist.png)

```
Input: head = [3,2,0,-4], pos = 1
Output: true
Explanation: There is a cycle in the linked list, where the tail connects to the 1st node (0-indexed).
```

**Example 2:**

![https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist_test2.png](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist_test2.png)

```
Input: head = [1,2], pos = 0
Output: true
Explanation: There is a cycle in the linked list, where the tail connects to the 0th node.
```

**Example 3:**

![https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist_test3.png](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist_test3.png)

```
Input: head = [1], pos = -1
Output: false
Explanation: There is no cycle in the linked list.
```

**Constraints:**

- The number of the nodes in the list is in the range `[0, 104]`.
- `105 <= Node.val <= 105`
- `pos` is `1` or a **valid index** in the linked-list.

### Solution

```kotlin
/**
 * Example:
 * var li = ListNode(5)
 * var v = li.`val`
 * Definition for singly-linked list.
 * class ListNode(var `val`: Int) {
 *     var next: ListNode? = null
 * }
 */

class Solution {
    fun hasCycle(head: ListNode?): Boolean {
        var head1 = head
        var head2 = head

        while(head1?.next != null && head2?.next?.next != null) {
            head1 = head1?.next
            head2 = head2?.next?.next
            if(head1 == head2)
                return true
        }

        return false
    }
}
```