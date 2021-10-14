## [第 N 个泰波那契数](https://leetcode-cn.com/problems/n-th-tribonacci-number/)

题目

```tex
泰波那契序列 Tn 定义如下： 

T0 = 0, T1 = 1, T2 = 1, 且在 n >= 0 的条件下 Tn+3 = Tn + Tn+1 + Tn+2

给你整数 n，请返回第 n 个泰波那契数 Tn 的值。
```

代码

解法一：递归

```java
class Solution {
    public int tribonacci(int n) {
        if (n<=0)
            return 0;
        if (n==1)
            return 1;
        if (n==2)
            return 1;
        return tribonacci(n-1)+tribonacci(n-2)+tribonacci(n-3);
    }
}
```

解法二：迭代（动态规划？）

```java
class Solution {
    public int tribonacci(int n) {
        if (n<=0)
            return 0;
        if (n==1)
            return 1;
        if (n==2)
            return 1;
        int i = 2, a = 1,b = 1, c = 0;
        while (i < n) {
            a = a+b+c;
            b = a-b-c;
            c = a-b-c;
            i++;
        }
        return a;
    }
}
```

解法三：矩阵快速幂(代码没看，反正就是矩阵相乘最后乘开始的三个数)

- 时间复杂度：O(logn)。
- 空间复杂度：O(1)。

```java
class Solution {
    public int tribonacci(int n) {
        if (n == 0) {
            return 0;
        }
        if (n <= 2) {
            return 1;
        }
        int[][] q = {{1, 1, 1}, {1, 0, 0}, {0, 1, 0}};
        int[][] res = pow(q, n);
        return res[0][2];
    }

    public int[][] pow(int[][] a, int n) {
        int[][] ret = {{1, 0, 0}, {0, 1, 0}, {0, 0, 1}};
        while (n > 0) {
            if ((n & 1) == 1) {
                ret = multiply(ret, a);
            }
            n >>= 1;
            a = multiply(a, a);
        }
        return ret;
    }

    public int[][] multiply(int[][] a, int[][] b) {
        int[][] c = new int[3][3];
        for (int i = 0; i < 3; i++) {
            for (int j = 0; j < 3; j++) {
                c[i][j] = a[i][0] * b[0][j] + a[i][1] * b[1][j] + a[i][2] * b[2][j];
            }
        }
        return c;
    }
}
```

