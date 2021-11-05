## [Day7-树的子结构](https://leetcode-cn.com/problems/shu-de-zi-jie-gou-lcof/)

题目

```tex
输入两棵二叉树A和B，判断B是不是A的子结构。(约定空树不是任意一个树的子结构)

B是A的子结构， 即 A中有出现和B相同的结构和节点值。
```

代码

```java
class Solution {
    public boolean isSubStructure(TreeNode A, TreeNode B) {
        if (B == null)
            return false;
        if (A!=null){
            if (A.val==B.val){
                return fun(A, B)||isSubStructure(A.left,B)||isSubStructure(A.right, B);
            }else{
                return isSubStructure(A.left,B)||isSubStructure(A.right, B);
            }
        }else{
            return false;
        }
    }
    public boolean fun(TreeNode a, TreeNode b){
        if (b==null)
            return true;
        if (a == null||a.val!=b.val)
            return false;
        return fun(a.left,b.left)&&fun(a.right,b.right);
    }
}
```

