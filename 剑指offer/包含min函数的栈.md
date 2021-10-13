#### 包含min函数的栈

题目

```txt
定义栈的数据结构，请在该类型中实现一个能够得到栈的最小元素的 min 函数在该栈中，调用 min、push 及 pop 的时间复杂度都是 O(1)。
```

代码

```java
class MinStack {
    Node head;
    Node head2;
    /** initialize your data structure here. */
    public MinStack() {
        head = new Node(Integer.MAX_VALUE);
        head.next = null;
        head2 = new Node(Integer.MAX_VALUE);
        head2.next = null;
    }

    public void push(int x) {
        int min;
        if (head2.next == null){
            min = x;
        }else{
            min = head2.next.data<x?head2.next.data:x;
        }
        Node node = new Node(x);
        node.next = head.next;
        head.next = node;

        Node node2 = new Node(min);
        node2.next = head2.next;
        head2.next = node2;
    }

    public void pop() {
        if (head.next == null) {
            return;
        }
        Node p = head.next;
        head.next = p.next;
        p.next = null;

        Node p2 = head2.next;
        head2.next = p2.next;
        p2.next = null;
    }

    public int top() {
        if (head.next != null) {
            return head.next.data;
        }
        return Integer.MAX_VALUE;
    }

    public int min() {
        if (head2.next != null) {
            return head2.next.data;
        }
        return Integer.MAX_VALUE;
    }
}
class Node{
    int data;
    Node next;
    public Node(int data){
        this.data = data;
        next = null;
    }
}
```