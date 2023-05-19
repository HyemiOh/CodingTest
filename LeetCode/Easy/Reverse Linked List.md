# Reverse Linked List

[Reverse Linked List - LeetCode](https://leetcode.com/problems/reverse-linked-list/description/)

### 문제 설명

Given the `head` of a singly linked list, reverse the list, and return *the reversed list*.

**Example 1:**

![https://assets.leetcode.com/uploads/2021/02/19/rev1ex1.jpg](https://assets.leetcode.com/uploads/2021/02/19/rev1ex1.jpg)

```
Input: head = [1,2,3,4,5]
Output: [5,4,3,2,1]
```

**Example 2:**

```
Input: head = [1,2]
Output: [2,1]
```

**Example 3:**

```
Input: head = []
Output: []
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
    fun reverseList(head: ListNode?): ListNode? {
        var current = head
        var prev: ListNode? = null

        while(current != null) {
            println("current: ${current.`val`} /// prev: ${prev?.`val`}")
            val next = current.next
            current.next = prev
            prev = current
            current = next
        }

        return prev
    }
}
```