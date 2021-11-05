## [II. 0～n-1中缺失的数字](https://leetcode-cn.com/problems/que-shi-de-shu-zi-lcof/)

题目

```tex
一个长度为n-1的递增排序数组中的所有数字都是唯一的，并且每个数字都在范围0～n-1之内。在范围0～n-1内的n个数字中有且只有一个数字不在该数组中，请找出这个数字。
```

代码

```java
class Solution {
    public int missingNumber(int[] nums) {
        int begin = 0, end = nums.length-1;
        while(begin<end){
            int mid = (begin+end)/2;
            if (nums[mid] == mid)
                begin = mid+1;
            else if (nums[mid]>mid)
                end = mid-1;
        }
        if(nums[begin] == begin)
            return begin+1;
        return begin;
    }
}
```

