## [21. 合并两个有序链表](https://leetcode-cn.com/problems/merge-two-sorted-lists/)
将两个有序链表合并为一个新的有序链表并返回。新链表是通过拼接给定的两个链表的所有节点组成的。 

示例：

输入：1->2->4, 1->3->4<br>
输出：1->1->2->3->4->4

#### 解题思路
```
class Solution:
    def mergeTwoLists(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """    
        ## dummy 记录新链表的head
        ## cur 记录当前结点
        dummy = cur = ListNode(0)
        ## 谁小cur.next指向谁，然后谁就往后移
        while l1 and l2:
            if l1.val < l2.val:
                cur.next = l1
                l1 = l1.next
            else:
                cur.next = l2
                l2 = l2.next
            # 子链表往后移，cur也往后移
            cur = cur.next
        # 当其中一个子链表的head指向nil，循环结束
        # cur把剩下没遍历完子链表连接起来
        cur.next = l1 or l2
        return dummy.next
```

