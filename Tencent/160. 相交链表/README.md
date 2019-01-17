## [160. 相交链表](https://leetcode-cn.com/problems/intersection-of-two-linked-lists/)
编写一个程序，找到两个单链表相交的起始节点。

#### 解题思路
```
 总体思路:
 A链遍历完，A头指针指向B链头指针
 B链遍历完，B头指针指向A链头
 如果有交点，此时A和B到交点的距离是相等的

class Solution(object):
    def getIntersectionNode(self, headA, headB):
        """
        :type head1, head1: ListNode
        :rtype: ListNode
        """
        if not headA or not headB:
            return None
        
        A, B = headA, headB
        while A != B:
            A = A.next if A else headB
            B = B.next if B else headA
        return A

```

```
另一种思路：
分别遍历A和B，得到lenA和lenB
长的链先走abs(lenA-lenB)的距离
然后A和B同时走，直到相遇

tempA, tempB = headA, headB
        lenA, lenB = 0, 0
        
        while tempA is not None:
            tempA = tempA.next
            lenA += 1
        
        while tempB is not None:
            tempB = tempB.next
            lenB += 1
            
        tempA, tempB = headA, headB
        
        if lenA > lenB:
            for i in range(lenA - lenB):
                tempA = tempA.next
        elif lenA < lenB:
            for i in range(lenB - lenA):
                tempB = tempB.next
        while tempA != tempB:
            tempA = tempA.next
            tempB = tempB.next
        return tempA

```