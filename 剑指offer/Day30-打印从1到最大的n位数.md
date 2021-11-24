## [Day30-打印从1到最大的n位数](https://leetcode-cn.com/problems/da-yin-cong-1dao-zui-da-de-nwei-shu-lcof/)

题目

```tex
输入数字 n，按顺序打印出从 1 到最大的 n 位十进制数。比如输入 3，则打印出 1、2、3 一直到最大的 3 位数 999。
```

代码

```java
class Solution {
    public int[] printNumbers(int n) {
        int max = 0;
        for (int i = 0; i < n; i++) {
            max=max*10+9;
        }
        int[] ints = new int[max];
        for (int i = 0; i < ints.length; i++) {
            ints[i] = i+1;
        }
        return ints;
    }
}
```



