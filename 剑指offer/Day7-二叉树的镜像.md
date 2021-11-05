## [Day7-二叉树的镜像](https://leetcode-cn.com/problems/er-cha-shu-de-jing-xiang-lcof/)

题目

```tex
请完成一个函数，输入一个二叉树，该函数输出它的镜像。
```

代码

```java
class Solution1 {
    public TreeNode mirrorTree(TreeNode root) {
        if (root == null)
            return null;
        else{
            TreeNode a = root.left;
            root.left = mirrorTree(root.right);
            root.right = mirrorTree(a);
            return root;
        }
    }
}
```

