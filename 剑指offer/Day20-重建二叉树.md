## [Day20-重建二叉树](https://leetcode-cn.com/problems/zhong-jian-er-cha-shu-lcof/)

题目

```tex
输入某二叉树的前序遍历和中序遍历的结果，请构建该二叉树并返回其根节点。

假设输入的前序遍历和中序遍历的结果中都不含重复的数字。
```

代码

```java
class Solution {
    public TreeNode buildTree(int[] preorder, int[] inorder) {
        return fun(preorder, inorder, 0, 0, preorder.length);
    }
    public TreeNode fun(int []preorder, int[] inorder, int left, int begin, int end) {
        if (left>preorder.length-1)
            return null;
        if (begin>=end)
            return null;
        int val = preorder[left];
        TreeNode treeNode = new TreeNode(val);
        int i = begin;
        while(i<end){
            if (inorder[i] == val)
                break;
            i++;
        }
        treeNode.left=fun(preorder,inorder,left+1,begin,i);
        treeNode.right=fun(preorder,inorder,left+i-begin+1,i+1,end);
        return treeNode;
    }
    public void midOrder(TreeNode root){
        if (root == null)
            return;
        System.out.println(root.val);
        midOrder(root.left);
        midOrder(root.right);
    }
}
```



