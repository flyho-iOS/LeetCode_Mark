## [413. Arithmetic Slices](https://leetcode.com/problems/arithmetic-slices/description/)
A sequence of number is called arithmetic if it consists of at least three elements and if the difference between any two consecutive elements is the same.(数组中等差递增子区间的个数)

###### 解题思路
```
class Solution(object):
    def numberOfArithmeticSlices(self, A):
        
        dp, diff = [0,0], 1
        for i in range(2,len(A)):
            if A[i]-A[i-1] == A[i-1]-A[i-2]:
                dp.append(dp[i-1]+diff)
                diff += 1 ## 如果连续，上一个数的结果+潜在可能连续的个数，然后潜在可能连续的个数+1
            else:
                dp.append(dp[i-1])
                diff = 1 ## 不连续，潜在可能连续的个数变为1，结果取上一个数的结果
        return dp[-1]
```
