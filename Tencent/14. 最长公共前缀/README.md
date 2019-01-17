## [14. 最长公共前缀](https://leetcode-cn.com/problems/longest-common-prefix/)

编写一个函数来查找字符串数组中的最长公共前缀。

如果不存在公共前缀，返回空字符串 ""。

##### 示例 1:
```
输入: ["flower","flow","flight"]
输出: "fl"
```
##### 示例 2:
```
输入: ["dog","racecar","car"]
输出: ""
解释: 输入不存在公共前缀。
```
##### 说明:
所有输入只包含小写字母 a-z 。


#### 解题思路
```
时间：28 ms，打败93.77% 的用户
Time:O(l * n) l为最短单词长度，n为单词个数
这是一种较为暴力的解法，总遍历次数为最短单词的长度
二级遍历每一个单词，比较当前遍历到第i个字符是否相同
不同直接返回ans，都相同就拼接到ans

class Solution(object):
    def longestCommonPrefix(self, strs):
        
        if not strs: 
        	return ''
        
		ans = ''
        minLen = float('inf')
        for s in strs:
            minLen = min(minLen, len(s))
        
        for i in range(minLen):
            t = strs[0][i]
            for s in strs:
                if not s[i] == t:
                    return ans
            ans += t
            
        return ans
```

```
这题还有其他思路，暂不实现（其实是水平不够写不出来 T_T）
1.通过把所有单词构建成trie字典树，那么第一个分支之前的就是所要的前缀（想是挺简单，trie树实现起来不简单）
```

