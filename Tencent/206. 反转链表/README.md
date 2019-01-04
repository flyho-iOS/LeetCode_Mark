## [206. 反转链表](https://leetcode-cn.com/problems/reverse-linked-list/)
反转一个单链表。

示例:

输入: 1->2->3->4->5->NULL
输出: 5->4->3->2->1->NULL <br>

#####进阶:
你可以迭代或递归地反转链表。你能否用两种方法解决这道题？

###### 解题思路
```
class Solution:
    def reverseList(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        
        # 迭代解法
        pre = None
        cur = head
        
        while cur:
            nxt = cur.next
            cur.next = pre
            pre = cur
            cur = nxt
        return pre
        
        ## 递归解法
        if not head or not head.next:
            return head
        node = self.reverseList(head.next)
        # 相邻两结点反转
        head.next.next = head
        head.next = None
        
        return node

```