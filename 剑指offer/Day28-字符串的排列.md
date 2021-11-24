## [Day28-字符串的排列](https://leetcode-cn.com/problems/zi-fu-chuan-de-pai-lie-lcof/)

题目

```tex
输入一个字符串，打印出该字符串中字符的所有排列。

你可以以任意顺序返回这个字符串数组，但里面不能有重复元素。
```

代码

```java
class Solution {
    char[] c;
    List<String> list = new LinkedList<>();
    public String[] permutation(String s) {
        this.c = s.toCharArray();
        dfs(0);
        return list.toArray(new String[0]);
    }
    public void dfs(int x){
        if (x == c.length-1){
            list.add(new String(c));
            return;
        }
        // 标记x位之后与当前x位已交换字符，相同字符无需交换
        Set<Character> set = new HashSet<>();
        for (int i = x; i< c.length; i++){
            if (set.contains(c[i]))
                continue;
            set.add(c[i]);
            swap(i,x);
            dfs(x+1);
            swap(i,x);
        }
    }
    public void swap(int i,int x){
        char b = c[i];
        c[i] = c[x];
        c[x] = b;
    }
}
```



