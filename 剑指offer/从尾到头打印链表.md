## [从尾到头打印链表](https://leetcode-cn.com/problems/cong-wei-dao-tou-da-yin-lian-biao-lcof/)

题目

```txt
输入一个链表的头节点，从尾到头反过来返回每个节点的值（用数组返回）。
```

代码

```java
class Solution {
        public int[] reversePrint(ListNode head) {
            ListNode node = head;
            int len = 0;
            while(node!=null){
                len++;
                node = node.next;
            }
            int a[] = new int[len];
            for (int i = len-1;i>=0;i--){
                a[i] = head.val;
                head = head.next;
            }
            return a;
        }
    }
```

