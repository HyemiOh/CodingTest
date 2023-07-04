# Check If It Is a Straight Line

[Check If It Is a Straight Line - LeetCode](https://leetcode.com/problems/check-if-it-is-a-straight-line/description/)

### Description

You are given an array `coordinates`, `coordinates[i] = [x, y]`, where `[x, y]` represents the coordinate of a point. Check if these points make a straight line in the XY plane.

**Example 1:**

!https://assets.leetcode.com/uploads/2019/10/15/untitled-diagram-2.jpg

```
Input: coordinates = [[1,2],[2,3],[3,4],[4,5],[5,6],[6,7]]
Output: true
```

**Example 2:**

!https://assets.leetcode.com/uploads/2019/10/09/untitled-diagram-1.jpg

```
Input: coordinates = [[1,1],[2,2],[3,4],[4,5],[5,6],[7,7]]
Output: false
```

**Constraints:**

- `2 <= coordinates.length <= 1000`
- `coordinates[i].length == 2`
- `10^4 <= coordinates[i][0], coordinates[i][1] <= 10^4`
- `coordinates` contains no duplicate point.

### Solution

```kotlin
class Solution {
    fun checkStraightLine(coordinates: Array<IntArray>): Boolean {
        val x = coordinates[0][0] - coordinates[1][0]
        val y = coordinates[0][1] - coordinates[1][1]

        for(i in 2..coordinates.lastIndex) {
            if(y * (coordinates[i - 1][0] - coordinates[i][0]) != x * (coordinates[i - 1][1] - coordinates[i][1])) {
                return false
            }
        }

        return true
    }
}
```