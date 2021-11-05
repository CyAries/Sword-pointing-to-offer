## [Day20-二叉搜索树的后序遍历序列](https://leetcode-cn.com/problems/er-cha-sou-suo-shu-de-hou-xu-bian-li-xu-lie-lcof/)

题目

```tex
输入一个整数数组，判断该数组是不是某二叉搜索树的后序遍历结果。如果是则返回 true，否则返回 false。假设输入的数组的任意两个数字都互不相同。
```

代码

```java
class Solution {
    public boolean verifyPostorder(int[] postorder) {
        Stack<Integer> stack = new Stack<>();
        int root = Integer.MAX_VALUE;
        for (int i = postorder.length-1; i >= 0; i--) {
            if (postorder[i]>root){
                return false;
            }
            while(!stack.isEmpty()&&stack.peek()>postorder[i]){
                root = stack.pop();
            }
            stack.add(postorder[i]);
        }
        return true;
    }
}
```



