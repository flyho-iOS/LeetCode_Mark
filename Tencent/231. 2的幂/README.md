## [231. 2的幂](https://leetcode-cn.com/problems/power-of-two/)
给定一个整数，编写一个函数来判断它是否是 2 的幂次方。

####示例 1:

输入: 1<br>
输出: true<br>
####示例 2:

输入: 16<br>
输出: true<br>
####示例 3:

输入: 218<br>
输出: false

#### 解题思路
```
class Solution:
    def isPowerOfTwo(self, n):
		## n 必须为大于零的正整数
		## 位运算技巧
		## 2的n次方的二进制只有最高位为1，其他为0
		## 例如 16      二进制 1 0000
		## 16-1 = 15   二进制 0 1111
		## 进行“与”操作 为0 的则是 2的n次方数
		return not n <= 0 and (n & (n - 1)) == 0
```