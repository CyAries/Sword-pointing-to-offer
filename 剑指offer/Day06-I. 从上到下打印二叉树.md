## [Day6-I. 从上到下打印二叉树](https://leetcode-cn.com/problems/cong-shang-dao-xia-da-yin-er-cha-shu-lcof/)

题目

```tex
从上到下打印出二叉树的每个节点，同一层的节点按照从左到右的顺序打印。
```

代码

```java
class Solution1 {
    public int[] levelOrder(TreeNode root) {
        Queue<TreeNode> queue = new LinkedList<>();
        List<Integer> list = new ArrayList<>();
        if (root!=null)
            queue.offer(root);
        while(!queue.isEmpty()){
            TreeNode pop = queue.poll();
            list.add(pop.val);
            TreeNode left = pop.left;
            TreeNode right = pop.right;
            if (left!=null)
                queue.offer(left);
            if (right!=null)
                queue.offer(right);
        }
        int[] a = new int[list.size()];
        for (int i = 0; i < a.length; i++) {
            a[i] = list.get(i);
        }
        return a;
    }
}
```

