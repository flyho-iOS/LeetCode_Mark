## [64. Minimum Path Sum](https://leetcode.com/problems/minimum-path-sum/description/)
Given a m x n grid filled with non-negative numbers, find a path from top left to bottom right which minimizes the sum of all numbers along its path.

Note: You can only move either down or right at any point in time.

###### Example:

Input:
```
[
  [1,3,1],
  [1,5,1],
  [4,2,1]
]
```

Output: 7
Explanation: Because the path 1→3→1→1→1 minimizes the sum.

###### 解题过程
```
class Solution:
    def minPathSum(self, grid):
        """
        :type grid: List[List[int]]
        :rtype: int
        """
        m = len(grid[0])
        n = len(grid)
        dp = [[1 for _ in range(m)] for _ in range(n)]
        for i in range(n):
            for j in range(m):
            	   # 到达grid[0][0]只能是其本身
                if i == 0 and j == 0:
                    dp[i][j] = grid[i][j]
                elif i == 0: # 第一行的只能从左边到达，所以dp[i][j-1]
                    dp[i][j] = dp[i][j-1]+grid[i][j]
                elif j == 0: # 第一列只能从上面到达，所以取dp[i-1][j]
                    dp[i][j] = dp[i-1][j]+grid[i][j]
                else: # 剩余的情况，取上面或左边之间的最小值
                    dp[i][j] = min(dp[i-1][j],dp[i][j-1])+grid[i][j]
        return dp[-1][-1]
```
