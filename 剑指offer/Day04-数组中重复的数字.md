## [数组中重复的数字](https://leetcode-cn.com/problems/shu-zu-zhong-zhong-fu-de-shu-zi-lcof/)

题目

```tex
找出数组中重复的数字。

在一个长度为 n 的数组 nums 里的所有数字都在 0～n-1 的范围内。数组中某些数字是重复的，但不知道有几个数字重复了，也不知道每个数字重复了几次。请找出数组中任意一个重复的数字。
```

代码

```java
class Solution {
    public int findRepeatNumber(int[] nums) {
        int[] ints = new int[nums.length];
        for (int num : nums) {
            ints[num]++;
        }
        int index = -1;
        for (int i = 0; i < ints.length; i++) {
            if (ints[i]>1){
                index = i;
                break;
            }
        }
        return index;
    }
}
```

