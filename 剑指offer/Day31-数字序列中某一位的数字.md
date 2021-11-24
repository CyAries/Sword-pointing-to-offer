## [Day31-数字序列中某一位的数字](https://leetcode-cn.com/problems/shu-zi-xu-lie-zhong-mou-yi-wei-de-shu-zi-lcof/)

题目

```tex
数字以0123456789101112131415…的格式序列化到一个字符序列中。在这个序列中，第5位（从下标0开始计数）是5，第13位是1，第19位是4，等等。

请写一个函数，求任意第n位对应的数字。
```

代码

```java
class Solution {
    public int findNthDigit(int n) {
        if (n<=9)
            return n;
        int a = 1, b = 9;// a位数，b:a位数的数量
        int m = n;
        n-=a*b;
        while(n>0){
            a+=1;
            b*=10;
            if (a*b<0) {
                m=n;
                break;
            }
            m = n;
            n -= a*b;
        }
        int begin = pow(10, a-1);
        return String.valueOf(begin + (m - 1) / a).charAt((m-1)%a)-'0';
        //char[] chars = String.valueOf(begin + (m - 1) / a).toCharArray();
        //char aChar = chars[(m - 1) % a];
        //return aChar-'0';
    }
    public int pow(int a,int b){
        int m = 1;
        while(b>0){
            m*=a;
            b--;
        }
        return m;
    }
}
```



