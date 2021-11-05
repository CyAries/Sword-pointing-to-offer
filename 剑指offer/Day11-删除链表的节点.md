## [Day11-删除链表的节点](https://leetcode-cn.com/problems/shan-chu-lian-biao-de-jie-dian-lcof/)

题目

```tex
给定单向链表的头指针和一个要删除的节点的值，定义一个函数删除该节点。

返回删除后的链表的头节点。
```

代码

```java
class Solution1 {
    public ListNode deleteNode(ListNode head, int val) {
        ListNode pre = new ListNode(-1);
        pre.next = head;
        ListNode p = head;
        head = pre;
        while(p!=null&&p.val!=val){
            pre = p;
            p = p.next;
        }
        if (p != null){
            pre.next = p.next;
        }
        return head.next;
    }
}
```

