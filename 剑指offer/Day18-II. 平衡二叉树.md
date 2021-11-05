## [Day18-II. 平衡二叉树](https://leetcode-cn.com/problems/ping-heng-er-cha-shu-lcof/)

题目

```tex
输入一棵二叉树的根节点，判断该树是不是平衡二叉树。如果某二叉树中任意节点的左右子树的深度相差不超过1，那么它就是一棵平衡二叉树。
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
    public boolean isBalanced(TreeNode root) {
        if (root == null)
            return true;
        return isBalanced(root.left)&&isBalanced(root.right)
            &&Math.abs(getDepth(root.left) - getDepth(root.right))<=1;
    }
    public int getDepth(TreeNode root){
        if (root == null)
            return 0;
        return Math.max(getDepth(root.left), getDepth(root.right))+1;
    }
}
```



