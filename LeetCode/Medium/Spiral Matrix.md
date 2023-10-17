# Spiral Matrix

[Spiral Matrix - LeetCode](https://leetcode.com/problems/spiral-matrix/)

### 문제 설명

Given an `m x n` `matrix`, return *all elements of the* `matrix` *in spiral order*.

**Example 1:**

![https://assets.leetcode.com/uploads/2020/11/13/spiral1.jpg](https://assets.leetcode.com/uploads/2020/11/13/spiral1.jpg)

```
Input: matrix = [[1,2,3],[4,5,6],[7,8,9]]
Output: [1,2,3,6,9,8,7,4,5]
```

**Example 2:**

![https://assets.leetcode.com/uploads/2020/11/13/spiral.jpg](https://assets.leetcode.com/uploads/2020/11/13/spiral.jpg)

```
Input: matrix = [[1,2,3,4],[5,6,7,8],[9,10,11,12]]
Output: [1,2,3,4,8,12,11,10,9,5,6,7]
```

**Constraints:**

- `m == matrix.length`
- `n == matrix[i].length`
- `1 <= m, n <= 10`
- `100 <= matrix[i][j] <= 100`

### 나의 풀이

```kotlin
class Solution {
    fun spiralOrder(matrix: Array<IntArray>): List<Int> {
        val answer = mutableListOf<Int>()
        var top = 0
        var left = 0
        var bottom = matrix.size - 1
        var right = matrix[0].size - 1
        var dir = 0
        while (top <= bottom && left <= right) {
            when (dir) {
                0 -> {
                    for (i in left until right + 1) {
                        answer.add(matrix[left][i])
                    }
                    top++
                }
                1 -> {
                    for (i in top until bottom + 1) {
                        answer.add(matrix[i][right])
                    }
                    right--
                }
                2 -> {
                    for (i in right downTo left) {
                        answer.add(matrix[bottom][i])
                    }
                    bottom--
                }
                3 -> {
                    for (i in bottom downTo top) {
                        answer.add(matrix[i][left])
                    }
                    left++
                }
            }
            dir = (dir + 1) % 4

        }
        return answer
    }
}
```