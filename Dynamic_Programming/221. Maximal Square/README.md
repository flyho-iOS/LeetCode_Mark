Given a 2D binary matrix filled with 0's and 1's, find the largest square containing only 1's and return its area.

Example:

Input: </br>
&ensp;&ensp;&ensp;&ensp;1 0 1 0 0</br>
&ensp;&ensp;&ensp;&ensp;1 0 1 1 1</br>
&ensp;&ensp;&ensp;&ensp;1 1 1 1 1</br>
&ensp;&ensp;&ensp;&ensp;1 0 0 1 0</br>
Output: 4

###### 解题思路
```
## 能否组成正方形 取决于最小的边 ，边必须大于1

class Solution(object):
    def maximalSquare(self, matrix):
        
        if not matrix:return 0
        
        ans = 0
        m, n = len(matrix), len(matrix[0])
        dp = [[0 for _ in range(n)] for _ in range(m)]
        for i in range(m):
            for j in range(n):
                dp[i][j] = int(matrix[i][j])
                if i and j and dp[i][j]:
                    dp[i][j] = min(dp[i-1][j-1],dp[i-1][j],dp[i][j-1])+1
                ans = max(ans,dp[i][j])
        return ans*ans
```
