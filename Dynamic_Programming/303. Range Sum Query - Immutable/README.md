Given an integer array nums, find the sum of the elements between indices i and j (i ≤ j), inclusive.

Example:
Given nums = [-2, 0, 3, -5, 2, -1]

sumRange(0, 2) -> 1<br>
sumRange(2, 5) -> -1<br>
sumRange(0, 5) -> -3<br>
Note:<br>
You may assume that the array does not change.<br>
There are many calls to sumRange function.

###### 解题思路

dp[i] 表示 0 ~ i 区间的和<br>
求某区间可以理解为：<br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;区间[2,4] = [0，4]（即dp[4]）的和 - [0,1]（即dp[1]）的和

```
class NumArray(object):
    def __init__(self, nums):
        self.dp = nums
        for i in range(1, len(nums)):
            self.dp[i] += self.dp[i-1]

    def sumRange(self, i, j):
        return self.dp[j] - (self.dp[i-1] if i > 0 else 0)
```
