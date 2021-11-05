## [Day9-连续子数组的最大和](https://leetcode-cn.com/problems/lian-xu-zi-shu-zu-de-zui-da-he-lcof/)

题目

```tex
输入一个整型数组，数组中的一个或连续多个整数组成一个子数组。求所有子数组的和的最大值。

要求时间复杂度为O(n)。
```

代码

```java
class Solution2 {
    public int maxSubArray(int[] nums) {
        int pre = 0,max = nums[0];
        for (int i = 0; i < nums.length; i++) {
            pre = Math.max(pre+nums[i], nums[i]);
            max = Math.max(pre, max);
        }
        return max;
    }
}
```

