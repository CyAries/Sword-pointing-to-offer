## [I. 在排序数组中查找数字 I](https://leetcode-cn.com/problems/zai-pai-xu-shu-zu-zhong-cha-zhao-shu-zi-lcof/)

题目

```tex
统计一个数字在排序数组中出现的次数。
```

代码

```java
class Solution {
    public int search(int[] nums, int target) {
        int index = searchIndex(nums, target);
        if (index == -1)
            return 0;
        int len = 1;
        for (int i = index-1;i>=0;i--){
            if (nums[i] == target)
                len++;
            else
                break;
        }
        for (int i = index+1;i<nums.length;i++){
            if (nums[i] == target)
                len++;
            else
                break;
        }
        return len;
    }
    public int searchIndex(int []nums, int target){
        int begin = 0, end = nums.length-1;
        while(begin<=end){
            int middle = (begin+end)/2;
            if (nums[middle] == target) {
                return middle;
            }else if(nums[middle]<target){
                begin = middle+1;
            }else{
                end = middle-1;
            }
        }
        return -1;
    }
}
```

