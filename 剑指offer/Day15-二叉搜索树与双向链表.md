## [Day15-二叉搜索树与双向链表](https://leetcode-cn.com/problems/er-cha-sou-suo-shu-yu-shuang-xiang-lian-biao-lcof/)

题目

```tex
输入一棵二叉搜索树，将该二叉搜索树转换成一个排序的循环双向链表。要求不能创建任何新的节点，只能调整树中节点指针的指向。
```

代码

```java
/*
// Definition for a Node.
class Node {
    public int val;
    public Node left;
    public Node right;

    public Node() {}

    public Node(int _val) {
        val = _val;
    }

    public Node(int _val,Node _left,Node _right) {
        val = _val;
        left = _left;
        right = _right;
    }
};
*/
class Solution {
    Node pre = new Node(),head = pre;
    public Node treeToDoublyList(Node root) {
        if (root == null)
            return null;
        midOrder(root);
        head.right.left = pre;
        pre.right = head.right;
        return head.right;
    }
    public void midOrder(Node node){
        if (node == null)
            return;
        midOrder(node.left);
        pre.right = node;
        node.left = pre;
        pre = node;
        midOrder(node.right);
    }
}
```



