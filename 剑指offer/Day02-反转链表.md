## [反转链表](https://leetcode-cn.com/problems/fan-zhuan-lian-biao-lcof/)

题目

```txt
定义一个函数，输入一个链表的头节点，反转该链表并输出反转后链表的头节点。
```

代码

头插法

```java
class Solution {
    public ListNode reverseList(ListNode head) {
        ListNode node = new ListNode(-1);
        node.next = null;
        ListNode p = head;
        while(p!=null){
            head = head.next;
            p.next = node.next;
            node.next = p;
            p = head;
        }
        return node.next;
    }
}
class ListNode{
    int val;
    ListNode next;
    ListNode(int x){
        val = x;
    }
}
```

