## [53. 最大子序和](https://leetcode-cn.com/problems/maximum-subarray/)

给定一个整数数组 nums ，找到一个具有最大和的连续子数组（子数组最少包含一个元素），返回其最大和。

##### 示例:
```
输入: [-2,1,-3,4,-1,2,1,-5,4],
输出: 6
解释: 连续子数组 [4,-1,2,1] 的和最大，为 6。
```
##### 进阶:

如果你已经实现复杂度为 O(n) 的解法，尝试使用更为精妙的分治法求解。


#### 解题思路
```
class Solution:
    def maxSubArray(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        ## 以 nums[0] 为初始最大值
        res = t = nums[0]
        for i in range(1,len(nums)):
            # 如果 nums[i] > t+nums[i]，表示最大值区间从i开始
            # 如果 nums[i] < t+nums[i]，表示最大值区间为之前的区间在包含i
            t = max(nums[i], t+nums[i])
            # 和上一个区间的和比较，取最大值
            res = max(t, res)
        return res
```