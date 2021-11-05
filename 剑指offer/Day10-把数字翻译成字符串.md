## [Day10-把数字翻译成字符串](https://leetcode-cn.com/problems/ba-shu-zi-fan-yi-cheng-zi-fu-chuan-lcof/)

题目

```tex
给定一个数字，我们按照如下规则把它翻译为字符串：0 翻译成 “a” ，1 翻译成 “b”，……，11 翻译成 “l”，……，25 翻译成 “z”。一个数字可能有多个翻译。请编程实现一个函数，用来计算一个数字有多少种不同的翻译方法。
```

代码

```java
class Solution1 {
    public int translateNum(int num) {
        if (num<10)
            return 1;
        else if(num<26)
            return 2;
        else{
            int i = num % 100;
            if (i<26)
                return translateNum(num/10)+translateNum(num/100);
            else
                return translateNum(num/10);
        }
    }
}
```

