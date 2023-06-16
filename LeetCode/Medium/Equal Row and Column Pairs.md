# Equal Row and Column Pairs

[Equal Row and Column Pairs - LeetCode](https://leetcode.com/problems/equal-row-and-column-pairs/description/?envType=study-plan-v2&envId=leetcode-75)

### Description

Given a **0-indexed** `n x n` integer matrix `grid`, *return the number of pairs* `(ri, cj)` *such that row* `ri` *and column* `cj` *are equal*.

A row and column pair is considered equal if they contain the same elements in the same order (i.e., an equal array).

**Example 1:**

!https://assets.leetcode.com/uploads/2022/06/01/ex1.jpg

```
Input: grid = [[3,2,1],[1,7,6],[2,7,7]]
Output: 1
Explanation: There is 1 equal row and column pair:
- (Row 2, Column 1): [2,7,7]

```

**Example 2:**

!https://assets.leetcode.com/uploads/2022/06/01/ex2.jpg

```
Input: grid = [[3,1,2,2],[1,4,4,5],[2,4,2,2],[2,4,2,2]]
Output: 3
Explanation: There are 3 equal row and column pairs:
- (Row 0, Column 0): [3,1,2,2]
- (Row 2, Column 2): [2,4,2,2]
- (Row 3, Column 2): [2,4,2,2]

```

**Constraints:**

- `n == grid.length == grid[i].length`
- `1 <= n <= 200`
- `1 <= grid[i][j] <= 105`

### Solution

```kotlin
class Solution {
    fun equalPairs(grid: Array<IntArray>): Int {
        var answer = 0
        val map = hashMapOf<List<Int>, Int>()

        grid.forEach {
            map[it.toMutableList()] = map.getOrDefault(it.toMutableList(), 0) + 1
        }

        for(i in grid.indices) {
            val array = mutableListOf<Int>()
            for(j in grid.indices) {
                array.add(grid[j][i])
            }
            answer += map.getOrDefault(array, 0)
        }

        return answer
    }
}
```