## [153. Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/description/)
Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.

(i.e.,  [0,1,2,4,5,6,7] might become  [4,5,6,7,0,1,2]).

Find the minimum element.

You may assume no duplicate exists in the array.

Example 1:

Input: [3,4,5,1,2] </br>
Output: 1
Example 2:

Input: [4,5,6,7,0,1,2]</br>
Output: 0

###### 解题思路
```
class Solution(object):
  def findMin(self, nums):

    i, j = 0, len(nums) - 1
    while i < j:
      m = i + (j - i) / 2
      if nums[m] > nums[j]:
        i = m + 1
      else:
        j = m
    return nums[i]
```
