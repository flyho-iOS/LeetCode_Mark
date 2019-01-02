## [198. House Robber](https://leetcode.com/problems/house-robber/description/)
You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security system connected and it will automatically contact the police if two adjacent houses were broken into on the same night. (简单讲就是相邻的房子不能抢)

Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight without alerting the police.

```
  例 [2,7,9,3,1]
   n    	     2  7   9   3   1
  抢(yes)	     2  7  11  10  12
  不抢(no)	     0  2   7  11  10
  
  由以上规律可得，yes = no + n,  no = max(yes,no)

```

```
    def rob(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if not nums:return 0
        
        yes, no = 0, 0
        for n in nums:
            no, yes = max(yes,no), n + no
        return max(yes,no)
```
