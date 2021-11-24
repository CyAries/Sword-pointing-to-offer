## [Day28-序列化二叉树](https://leetcode-cn.com/problems/xu-lie-hua-er-cha-shu-lcof/)

题目

```tex
请实现两个函数，分别用来序列化和反序列化二叉树。

你需要设计一个算法来实现二叉树的序列化与反序列化。这里不限定你的序列 / 反序列化算法执行逻辑，你只需要保证一个二叉树可以被序列化为一个字符串并且将这个字符串反序列化为原始的树结构。
```

代码

```java
public class Codec {
    String str = "";
    // Encodes a tree to a single string.
    public String serialize(TreeNode root) {
        rserialize(root);
        return str;
    }
    public void rserialize(TreeNode node){
        if (node == null) {
            str += "none,";
            return;
        }
        str = str+node.val+",";
        rserialize(node.left);
        rserialize(node.right);
    }
    // Decodes your encoded data to tree.
    public TreeNode deserialize(String data) {
        String[] split = data.split(",");
        List<String> strings = new ArrayList<>(Arrays.asList(split));
        TreeNode rdeserialize = rdeserialize(strings);
        return rdeserialize;
    }
    public TreeNode rdeserialize(List<String> list){
        if (list.get(0).equals("none")){
            list.remove(0);
            return null;
        }
        TreeNode node = new TreeNode(Integer.parseInt(list.get(0)));
        list.remove(0);
        node.left = rdeserialize(list);
        node.right = rdeserialize(list);
        return node;
    }
}
```



