## [Day15-二叉树中和为某一值的路径](https://leetcode-cn.com/problems/er-cha-shu-zhong-he-wei-mou-yi-zhi-de-lu-jing-lcof/)

题目

```tex
给你二叉树的根节点 root 和一个整数目标和 targetSum ，找出所有 从根节点到叶子节点 路径总和等于给定目标和的路径。

叶子节点 是指没有子节点的节点。
```

代码

```java
class Solution {
    List<List<Integer>> lists = new ArrayList<>();
    public List<List<Integer>> pathSum(TreeNode root, int target) {
        List<Integer> list = new ArrayList<>();
        midOrder(root, target, list);
        return lists;
    }
    public void midOrder(TreeNode root, int k, List<Integer> list){
        if (root==null)
            return;
        list.add(root.val);
        if (root.left==null&&root.right==null){
            if (k==root.val){
                List<Integer> list1 = new ArrayList<>(list);
                lists.add(list1);
            }
            list.remove((Integer) root.val);
            return;
        }
        midOrder(root.left, k-root.val, list);
        midOrder(root.right, k-root.val, list);
        list.remove((Integer) root.val);
    }
}
```



