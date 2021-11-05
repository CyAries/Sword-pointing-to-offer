## [Day12-合并两个排序的链表](https://leetcode-cn.com/problems/he-bing-liang-ge-pai-xu-de-lian-biao-lcof/)

题目

```tex
输入两个递增排序的链表，合并这两个链表并使新链表中的节点仍然是递增排序的。
```

代码

```java
class Solution1 {
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        ListNode head = new ListNode(-1);
        ListNode p = head;
        while(l1!=null&&l2!=null){
            if (l1.val>l2.val){
                p.next = l2;
                p = l2;
                l2 = l2.next;
            }else{
                p.next = l1;
                p = l1;
                l1 = l1.next;
            }
        }
        if (l1 != null) {
            p.next = l1;
        }
        if (l2 != null) {
            p.next = l2;
        }
        return head.next;
    }
}
```

