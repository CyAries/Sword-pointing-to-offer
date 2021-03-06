## [复杂链表的复制](https://leetcode-cn.com/problems/fu-za-lian-biao-de-fu-zhi-lcof/)

题目

```
请实现 copyRandomList 函数，复制一个复杂链表。在复杂链表中，每个节点除了有一个 next 指针指向下一个节点，还有一个 random 指针指向链表中的任意节点或者 null。
```

代码

解法一：递归

```java
class Solution {
    Map<Node, Node> map = new HashMap<>();
    public Node copyRandomList(Node head) {
        if (head == null)
            return null;
        if (!map.containsKey(head)){
            Node node = new Node(head.val);
            map.put(head, node);
            node.next = copyRandomList(head.next);
            node.random = copyRandomList(head.random);
        }
        return map.get(head);
    }
}
```

解法二：将新链表与老链表拼一起，创建完再拆开：`A->A'->B->B'->C->C'`

```java
class Solution {
    public Node copyRandomList(Node head) {
        if (head == null)
            return null;
        Node node = head;
        while(node!=null){
            Node newNode = new Node(node.val);
            newNode.next = node.next;
            node.next = newNode;
            node = node.next.next;
        }
        node = head;
        while(node!=null){
            if(node.random ==null){
                node.next.random = null;
            }else{
                node.next.random = node.random.next;
            }
            node = node.next.next;
        }
        node = head;
        Node p = node.next;
        Node head2 = p;
        while(node!=null){
            node.next = node.next.next;
            node = node.next;
            if(p.next!=null){
                p.next = p.next.next;
                p = p.next;
            }

        }
        return head2;
    }
}
```

