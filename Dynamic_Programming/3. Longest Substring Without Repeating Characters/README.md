## [3. Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)
Given a string, find the length of the longest substring without repeating characters.(找出字符串最长不重复的字符串)

###### 解题思路
```
class Solution:
    def lengthOfLongestSubstring(self, s):
        """
        :type s: str
        :rtype: int
        """
        ## dict 记录字符出现的index
        dic = {}
        start = maxLen = 0
        for i in range(len(s)):
            c = s[i]
            ## 当出现重复字符，计算当前的长度，更新字符串开始计算的index，为重复出现的下一位
            if c in dic and start <= dic[c]:
                maxLen = max(maxLen,i-start)
                start = dic[c]+1
            else:
            	## 如无重复，+1
                maxLen = max(maxLen,i-start+1)
            dic[c] = i
        
        return maxLen

```
