## [Day22-I. 数组中数字出现的次数](https://leetcode-cn.com/problems/shu-zu-zhong-shu-zi-chu-xian-de-ci-shu-lcof/)

题目

```tex
一个整型数组 nums 里除两个数字之外，其他数字都出现了两次。请写程序找出这两个只出现一次的数字。要求时间复杂度是O(n)，空间复杂度是O(1)。
```

代码

```java
class Solution {
    public int[] singleNumbers(int[] nums) {
        int ret=0;
        for (int num : nums) {
            ret^=num;
        }
        int div = 1;
        while ((div & ret) == 0) {
            div<<=1;
        }
        int[]a = new int[2];
        for (int num : nums) {
            if ((num&div)==0)
                a[0]^=num;
            else
                a[1]^=num;
        }
        return a;
    }
}
```



