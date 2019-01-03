## [104. 二叉树的最大深度](https://leetcode-cn.com/problems/maximum-depth-of-binary-tree/)

给定一个二叉树，找出其最大深度。

二叉树的深度为根节点到最远叶子节点的最长路径上的节点数。

说明: 叶子节点是指没有子节点的节点。

示例：<br>
给定二叉树 [3,9,20,null,null,15,7]，

![](tc-104.png)

返回它的最大深度 3 。

#### 解题
```
class Solution:
    def maxDepth(self, root):
        """
        :type root: TreeNode
        :rtype: int
        """
        ## 使用DFS
        ## 递归
        # if not root: 
        #     return 0
        # else:
        #     left_h = self.maxDepth(root.left)
        #     right_h = self.maxDepth(root.right)
        #     return max(left_h, right_h)+1
        
        ## 迭代
        if not root: return 0
        
        stack = [(root, 1)]
        maxDepth = 0
        while stack:
            node, depth = stack.pop()
			maxDepth = max(maxDepth,depth)
            if node.left: stack.append((node.left, depth+1)) 
            if node.right: stack.append((node.right, depth+1)) 
        
        return maxDepth
```
