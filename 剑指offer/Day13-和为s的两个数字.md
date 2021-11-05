## [Day13-和为s的两个数字](https://leetcode-cn.com/problems/he-wei-sde-liang-ge-shu-zi-lcof/)

题目

```tex
输入一个递增排序的数组和一个数字s，在数组中查找两个数，使得它们的和正好是s。如果有多对数字的和等于s，则输出任意一对即可。
```

代码

```java
class Solution2 {
    public int[] twoSum(int[] nums, int target) {
        int begin = 0, end = nums.length-1;
        while(begin<end){
            if (nums[begin]+nums[end]<target){
                begin++;
            }else if(nums[begin]+nums[end]>target){
                end--;
            }else{
                return new int[]{nums[begin],nums[end]};
            }
        }
        return null;
    }
}
```



