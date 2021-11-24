## [Day29-丑数](https://leetcode-cn.com/problems/chou-shu-lcof/)

题目

```tex
我们把只包含质因子 2、3 和 5 的数称作丑数（Ugly Number）。求按从小到大的顺序的第 n 个丑数。
```

代码

```java
class Solution {
    public int nthUglyNumber(int n) {
        int[] dp = new int[n];
        int a = 0,b = 0, c = 0;
        dp[0] = 1;
        for (int i = 1; i < n; i++) {
            int min = Math.min(dp[a]*2,dp[b]*3);
            dp[i] = Math.min(min,dp[c]*5);
            if (dp[i] == dp[a]*2)
                a++;
            if (dp[i] == dp[b]*3)
                b++;
            if (dp[i] == dp[c]*5)
                c++;
        }
        return dp[n-1];
    }
}
```



