## [Day13-调整数组顺序使奇数位于偶数前面](https://leetcode-cn.com/problems/diao-zheng-shu-zu-shun-xu-shi-qi-shu-wei-yu-ou-shu-qian-mian-lcof/)

题目

```tex
输入一个整数数组，实现一个函数来调整该数组中数字的顺序，使得所有奇数在数组的前半部分，所有偶数在数组的后半部分。
```

代码

```java
class Solution1 {
    public int[] exchange(int[] nums) {
        int begin = 0, end = nums.length-1;
        while(begin<end){
            while(begin<end){
                if (nums[begin]%2==0)
                    break;
                begin++;
            }
            while(begin<end){
                if (nums[end]%2==1)
                    break;
                end--;
            }
            if (begin<end) {
                int flag = nums[begin];
                nums[begin] = nums[end];
                nums[end] = flag;
            }
        }
        return nums;
    }
}
```



