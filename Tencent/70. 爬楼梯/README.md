## [70. 爬楼梯](https://leetcode-cn.com/problems/climbing-stairs/)
假设你正在爬楼梯。需要 n 阶你才能到达楼顶。

每次你可以爬 1 或 2 个台阶。你有多少种不同的方法可以爬到楼顶呢？

注意：给定 n 是一个正整数。

#### 解题思路

```
class Solution:
    def climbStairs(self, n):
        """
        :type n: int
        :rtype: int
        """
        
        '''
            0       1       2         3            4
           (0)     (1)  -> (1,1) -> (1,1,1) ->  (1,1,1,1)
                    |       (2)  ->  (2,1)  ->   (2,1,1)
                    |--------|-----> (1,2)  ->   (1,2,1)
                             |-----------------> (2,2)
        '''
        ## 由上图可知，0和1阶只有1种情况，从2阶开始，可以发现规律n阶的走法是从n-1阶和n-2阶的情况下衍生出来
        ## 类似斐波拉契函数 f(n) = f(n-1)+f(n-2)
        if n == 0 or n == 1:
            return 1
        
        dp = [0 for _ in range(n+1)]
        dp[0], dp[1] = 1, 1
        
        for i in range(2,n+1):
            dp[i] = dp[i-1]+dp[i-2]
        return dp[-1]
        
        ## 这种动态规划可以进行空间优化 空间复杂度：O(n) -> O(1)
        ans = 0
        n_1 = n_2 = 1
        for i in range(2,n+1):
            ans = n_1 + n_2
            n_1, n_2 = n_2, ans
        return ans
        
```