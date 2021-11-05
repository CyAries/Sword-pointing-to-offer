## [Day6-II. 从上到下打印二叉树 II](https://leetcode-cn.com/problems/cong-shang-dao-xia-da-yin-er-cha-shu-ii-lcof/)

题目

```tex
从上到下按层打印二叉树，同一层的节点按从左到右的顺序打印，每一层打印到一行。
```

代码

```java
class Solution2 {
    public List<List<Integer>> levelOrder(TreeNode root) {
        LinkedList<TreeNode> queue = new LinkedList<>();
        List<List<Integer>> list = new ArrayList<>();
        if (root!=null)
            queue.offer(root);
        while(!queue.isEmpty()){
            LinkedList<TreeNode> newQueue = new LinkedList<>();
            ArrayList<Integer> newList = new ArrayList<>();
            while(!queue.isEmpty()){
                TreeNode poll = queue.poll();
                newList.add(poll.val);
                TreeNode left = poll.left;
                TreeNode right = poll.right;
                if (left!=null)
                    newQueue.offer(left);
                if (right!=null)
                    newQueue.offer(right);
            }
            list.add(newList);
            queue = newQueue;
        }
        return list;
    }
}
```

