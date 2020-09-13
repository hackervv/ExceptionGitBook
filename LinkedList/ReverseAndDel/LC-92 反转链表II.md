#### LC-92 反转链表II

------

【难度】 ⭐ ⭐ 

【题目】

反转从位置 *m* 到 *n* 的链表。请使用一趟扫描完成反转。

**说明:**
1 ≤ *m* ≤ *n* ≤ 链表长度。

###### 解法一：拆分-反转-合并

1.  如果head为None，直接返回None。声明result作为伪头节点方便返回结果，声明res作为往后移动的节点。
2.  res向后移动m-1位，此时res为开始反转的节点，pre为反转节点前一个节点。
3.  声明back为现在的res，方便反转后指针连接，申明tmp1，tmp2 都为None，反转链表使用。
4.  tmp1 保存为res下一个节点，res指向tmp2(最开始为None),更新tmp2为res，res为tmp1。
5.  循环步骤4 n-m，完成部分反转。此时tmp1 为最后一个需要反转的下一个节点，tmp2为反转后的头节点。
6.  反转前一段最后节点pre接上反转后的头节点tmp2，反转后的尾节点接上反转后面一段的第一个节点。

```python
class Solution:
    def reverseBetween(self, head:ListNode, m:int, n:int):
        if not head:
            return None
        result = ListNode(0)
        result.next = head
        res = result
        for _ in range(m):
            pre = res
            res = res.next
        back = res
        tmp1 = None
        tmp2 = None
        for i in range(n - m + 1):
            tmp1 = res.next
            res.next = tmp2
            tmp2 = res
        	res = tmp1
        pre.next = tmp2
        back.next = tmp1
        return result.next
```

