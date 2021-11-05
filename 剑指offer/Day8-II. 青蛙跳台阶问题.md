## [Day8-II. 青蛙跳台阶问题](https://leetcode-cn.com/problems/qing-wa-tiao-tai-jie-wen-ti-lcof/)

题目

```tex
一只青蛙一次可以跳上1级台阶，也可以跳上2级台阶。求该青蛙跳上一个 n 级的台阶总共有多少种跳法。

答案需要取模 1e9+7（1000000007），如计算初始结果为：1000000008，请返回 1。
```

代码

```java
class Solution2 {
    public int numWays(int n) {
        if (n <= 1)
            return 1;
        int a = 2, b = 1,k = 2;
        while (k < n) {
            int c = a+b;
            b = a;
            a = c%1000000007;
            k++;
        }
        return a;
    }
}
```

