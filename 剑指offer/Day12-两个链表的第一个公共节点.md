## [Day12-两个链表的第一个公共节点](https://leetcode-cn.com/problems/liang-ge-lian-biao-de-di-yi-ge-gong-gong-jie-dian-lcof/)

题目

```tex
输入两个链表，找出它们的第一个公共节点。
```

代码

```java
public class Solution2 {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        HashSet<ListNode> listNodes = new HashSet<>();
        ListNode p = headA;
        while (p != null) {
            listNodes.add(p);
            p = p.next;
        }
        p = headB;
        while(p!=null){
            if (listNodes.contains(p))
                return p;
            p = p.next;
        }
        return null;
    }
}
```

```java
public class Solution {
        public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
            ListNode p1 = headA, p2 = headB;
            while(p1!=p2){
                if (p1 == null) {
                    p1 = headB;
                    p2 = p2.next;
                }else if (p2 == null) {
                    p2 = headA;
                    p1 = p1.next;
                }else {
                    p1 = p1.next;
                    p2 = p2.next;
                }
            }
            if (p1 == null)
                return null;
            else
                return p1;
        }
    }
```

