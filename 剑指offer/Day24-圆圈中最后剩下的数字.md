## [Day24-圆圈中最后剩下的数字](https://leetcode-cn.com/problems/yuan-quan-zhong-zui-hou-sheng-xia-de-shu-zi-lcof/)

题目

```tex
0,1,···,n-1这n个数字排成一个圆圈，从数字0开始，每次从这个圆圈里删除第m个数字（删除后从下一个数字开始计数）。求出这个圆圈里剩下的最后一个数字。

例如，0、1、2、3、4这5个数字组成一个圆圈，从数字0开始每次删除第3个数字，则删除的前4个数字依次是2、0、4、1，因此最后剩下的数字是3。
```

代码

```java
class Solution {
    public int lastRemaining(int n, int m) {
        int x = 0, a = 2;
        while(a<=n){
            x = (x+m)%a;
            a++;
        }
        return x;
    }
}
```

```java
class Solution3 {
    public int lastRemaining(int n, int m) {
        if (n == 1)
            return 0;
        int x = lastRemaining(n-1, m);
        return (x+m)%n;
    }
}
```

