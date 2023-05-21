# Merge Two Sorted Lists

[Merge Two Sorted Lists - LeetCode](https://leetcode.com/problems/merge-two-sorted-lists/description/)

### 문제 설명

You are given the heads of two sorted linked lists `list1` and `list2`.

Merge the two lists in a one **sorted** list. The list should be made by splicing together the nodes of the first two lists.

Return *the head of the merged linked list*.

**Example 1:**

![https://assets.leetcode.com/uploads/2020/10/03/merge_ex1.jpg](https://assets.leetcode.com/uploads/2020/10/03/merge_ex1.jpg)

```
Input: list1 = [1,2,4], list2 = [1,3,4]
Output: [1,1,2,3,4,4]
```

**Example 2:**

```
Input: list1 = [], list2 = []
Output: []
```

**Example 3:**

```
Input: list1 = [], list2 = [0]
Output: [0]
```

### 나의 풀이

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
    fun mergeTwoLists(list1: ListNode?, list2: ListNode?): ListNode? {
        val answer = ListNode(0)
        var newList1 = list1
        var newList2 = list2
        var current = answer

        while(newList1 != null && newList2 != null) {
            if(newList1.`val` < newList2.`val`) {
                current.next = newList1
                newList1 = newList1.next
            }
            else {
                current.next = newList2
                newList2 = newList2.next
            }
            current = current.next
        }

        if(newList1 != null) current.next = newList1
        if(newList2 != null) current.next = newList2
        
        return answer.next
    }
}
```