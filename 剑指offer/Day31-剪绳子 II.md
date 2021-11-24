## [Day31-剪绳子 II](https://leetcode-cn.com/problems/jian-sheng-zi-ii-lcof/)

题目

```tex
给你一根长度为 n 的绳子，请把绳子剪成整数长度的 m 段（m、n都是整数，n>1并且m>1），每段绳子的长度记为 k[0],k[1]...k[m - 1] 。请问 k[0]*k[1]*...*k[m - 1] 可能的最大乘积是多少？例如，当绳子的长度是8时，我们把它剪成长度分别为2、3、3的三段，此时得到的最大乘积是18。

答案需要取模 1e9+7（1000000007），如计算初始结果为：1000000008，请返回 1
```

代码

```java
class Solution {
        public int cuttingRope(int n) {
            if (n <= 2)
                return 1;
            if (n == 3)
                return 2;
            int i = n / 3;
            int j = n % 3;
            if (j == 0){
                return (int) pow(3,i);
            }else if (j == 1)
                return (int) (pow(3,i-1)*4%1000000007);
            else
                return (int) (pow(3,i)*2%1000000007);
        }
        public long pow(int a,int b){
            long ret = 1;
            while(b>0){
                ret=ret*a%1000000007;
                b--;
            }
            return ret;
        }
    }
```

2021/11/24

```java
class Solution5 {
    public int countDigitOne(int n) {
        int length = String.valueOf(n).length();
        int k = 1, ret = 0;
        for (int i = 0;i<length;i++){
            if (i == length-1){
                int i1 = n / k;
                if (i1>1){
                    ret+=k;
                }else{
                    ret+=(n%k+1);
                }
                break;
            }
            int i1 = n / (k * 10);
            int i2 = n % (k * 10);
            int i3 = i2 / k;
            if (i3 == 0)
                ret+=i1*k;
            else if (i3 == 1)
                ret+=i1*k+(i2%k+1);
            else
                ret+=(i1+1)*k;
            k*=10;
        }
        return ret;
    }
}
```