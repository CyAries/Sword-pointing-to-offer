## [Day7-对称的二叉树](https://leetcode-cn.com/problems/dui-cheng-de-er-cha-shu-lcof/)

题目

```tex
请实现一个函数，用来判断一棵二叉树是不是对称的。如果一棵二叉树和它的镜像一样，那么它是对称的。
```

代码

```java
class Solution2 {
        public boolean isSymmetric(TreeNode root) {
            return root == null || fun(root.left, root.right);
        }
        public boolean fun(TreeNode left, TreeNode right){
            if (left == null&&right == null)
                return true;
            else if(left==null||right ==null||left.val!=right.val)
                return false;
            else
                return fun(left.left,right.right)&&fun(left.right, right.left);
        }
    }
```

