## [20. 有效的括号](https://leetcode-cn.com/problems/valid-parentheses/)

给定一个只包括 '('，')'，'{'，'}'，'['，']' 的字符串，判断字符串是否有效。

有效字符串需满足：

```
	1.左括号必须用相同类型的右括号闭合。
	2.左括号必须以正确的顺序闭合。
```

注意空字符串可被认为是有效字符串。

#### 解题思路
```
class Solution:
    def isValid(self, s):
        """
        :type s: str
        :rtype: bool ([{}])
        """
        # 利用栈“后进先出”的特点
        # dict 为了方便配对验证
        dic = {'(':')', '[':']', '{':'}'}
        stack = []
        for c in s:
        	# 如果是左括号，就push到栈中
            if c == '(' or c == '[' or c == '{':
                stack.append(c)
          # 如果是右括号，栈进行pop，与c进行配对
            elif c == ')' or c == ']' or c == '}':
                ## 如果栈为空，就配对失败
                if not stack:
                    return False
                t = stack.pop()
                if not dic.get(t) == c:
                    return False
        ## 字符串遍历结束后，如果栈不为空，代表还有不能被配对的字符
        if stack: return False
        return True
```