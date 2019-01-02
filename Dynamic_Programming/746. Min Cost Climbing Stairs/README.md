On a staircase, the i-th step has some non-negative cost cost[i] assigned (0 indexed).Once you pay the cost, you can either climb one or two steps. You need to find minimum cost to reach the top of the floor, and you can either start from the step with index 0, or the step with index 1.（给定一个数组，数组中都是非负整数，踩在一个梯级上就要花钱，可以一次走一步或者两步，计算到达尽头时最小的花费是多少）

###### Example 1:
* Input: cost = [10, 15, 20]  
* output: 15  
* Explanation: Cheapest is start on cost[1], pay that cost and go to the top.

```
例 cost = [2,7,9,3,1]
    n    	  start   2  7   9   3   1   end
  走(yes)	     	  0  0   2   7  10
  
```
###### 解题过程
```
     def minCostClimbingStairs(self, cost):
        dp0, dp1, dp2 = 0, 0, 0
        for i in range(2,len(cost)+1):
            dp0 = min(dp1+cost[i-1],dp2+cost[i-2])
            dp1, dp2 = dp0, dp1
        return dp0
```
