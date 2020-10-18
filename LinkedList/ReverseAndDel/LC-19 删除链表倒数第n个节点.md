#### LC-19 删除链表倒数第n个节点

------

【难度】 ⭐ ⭐ 

【题目】

给定一个链表，删除链表的倒数第 n 个节点，并且返回链表的头结点。

示例：

给定一个链表: 1->2->3->4->5, 和 n = 2.

当删除了倒数第二个节点后，链表变为 1->2->3->5.
说明：

给定的 n 保证是有效的。

进阶：

你能尝试使用一趟扫描实现吗？

###### 解法一：快慢指针法

1.  判断head节点或者其下一个节点是否为None，为None则返回None。
2.  声明伪头节点dummy并将其指向head头节点，申明快指针和慢指针fast，slow 分别为head。
3.  快指针向后移动一位，n减1，直到n=0为止。
4.  申明tmp=slow，方便后续删除节点操作。快指针和慢指针同时向后移动，直到快指针为None。
5.  判断当前 tmp 和 slow是否相等，如果相等则表明需要删除头节点，伪头节点dummy指向头节点head的下一位。不相等则tmp的下一节点指向slow的下一个节点。
6.  返回dummy.next。

```python
class Solution:
    def removeNthFromEnd(self, head:ListNode, n:int) -> ListNode:
        if not head or not head.next:
            return None
        dummy = ListNode(-1)
        dummy.next = head
        slow = head
        fast = head
        while n > 0:
            fast = fast.next
            n -= 1
        tmp = slow
        while fast:
            tmp = slow
            fast = fast.next
            slow = slow.next
        if tmp == slow:
            dummy.next = head.next
        else:
            tmp.next = slow.next
        return dummy.next

```

