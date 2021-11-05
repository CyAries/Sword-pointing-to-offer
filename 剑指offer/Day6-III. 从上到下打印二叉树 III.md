## [Day6-III. 从上到下打印二叉树 III](https://leetcode-cn.com/problems/cong-shang-dao-xia-da-yin-er-cha-shu-iii-lcof/)

题目

```tex
请实现一个函数按照之字形顺序打印二叉树，即第一行按照从左到右的顺序打印，第二层按照从右到左的顺序打印，第三行再按照从左到右的顺序打印，其他行以此类推。
```

代码

```java
class Solution {
    public List<List<Integer>> levelOrder(TreeNode root) {
        List<List<Integer>> list = new ArrayList<>();
        Stack<TreeNode> stack = new Stack<>();
        int i = 1;
        if (root!=null)
            stack.push(root);
        List<Integer> newList;
        while(!stack.isEmpty()){
            newList = new ArrayList<>();
            Stack<TreeNode> newStack = new Stack<>();
            while (!stack.isEmpty()) {
                TreeNode poll = stack.pop();
                newList.add(poll.val);
                if (i%2 == 1) {
                    if (poll.left != null)
                        newStack.push(poll.left);
                    if (poll.right != null)
                        newStack.push(poll.right);
                } else {
                    if (poll.right != null)
                        newStack.push(poll.right);
                    if (poll.left != null)
                        newStack.push(poll.left);
                }
            }
            stack = newStack;
            list.add(newList);
            i++;
        }
        return list;
    }
}
```

