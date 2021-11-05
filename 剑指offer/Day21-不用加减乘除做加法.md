## [Day21-不用加减乘除做加法](https://leetcode-cn.com/problems/bu-yong-jia-jian-cheng-chu-zuo-jia-fa-lcof/)

题目

```tex
写一个函数，求两个整数之和，要求在函数体内不得使用 “+”、“-”、“*”、“/” 四则运算符号。
```

代码

```java
class Solution {
    public int add(int a, int b) {
        while(b!=0){
            int c = (a&b)<<1;
            a ^= b;
            b = c;
        }
        return a;
    }
}
```



