## [646. Maximum Length of Pair Chain](https://leetcode.com/problems/maximum-length-of-pair-chain/description/)
You are given n pairs of numbers. In every pair, the first number is always smaller than the second number.

Now, we define a pair (c, d) can follow another pair (a, b) if and only if b < c. Chain of pairs can be formed in this fashion.

Given a set of pairs, find the length longest chain which can be formed. You needn't use up all the given pairs. You can select pairs in any order.

###### Example 1: 
	Input: [[1,2], [2,3], [3,4]]
	Output: 2
	Explanation: The longest chain is [1,2] -> [3,4]
	
###### 解题过程
```
O(nlogn)
class Solution:
    def findLongestChain(self, pairs):        
        cur, res = float('-inf'), 0
        # 遍历排序好的pairs
        for p in sorted(pairs, key=lambda x: x[1]):
            if cur < p[0]: 
                cur, res = p[1], res + 1
        return res
```
