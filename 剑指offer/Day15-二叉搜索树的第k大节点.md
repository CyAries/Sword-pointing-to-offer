## [Day15-二叉搜索树的第k大节点](https://leetcode-cn.com/problems/er-cha-sou-suo-shu-de-di-kda-jie-dian-lcof/)

题目

```tex
给定一棵二叉搜索树，请找出其中第k大的节点
```

代码

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    int res,k;
    public int kthLargest(TreeNode root, int k) {
        this.k = k;
        preOrder(root);
        return res;
    }
    public void preOrder(TreeNode node){
        if (node == null||k == 0)
            return;
        preOrder(node.right);
        if(--k==0){
            res = node.val;
            return;
        }
        preOrder(node.left);
    }
}
```



