## [Day16-把数组排成最小的数](https://leetcode-cn.com/problems/ba-shu-zu-pai-cheng-zui-xiao-de-shu-lcof/)

题目

```tex
输入一个非负整数数组，把数组里所有数字拼接起来排成一个数，打印能拼接出的所有数字中最小的一个。
```

代码

```java
class Solution {
    public String minNumber(int[] nums){
        String[] strs = new String[nums.length];
        for (int i = 0; i < nums.length; i++) {
            strs[i] = String.valueOf(nums[i]);
        }
        quickSort(strs, 0, nums.length-1);
        return String.join("", strs);
    }
    public void quickSort(String[] strs, int l, int r) {
        if (l>=r)
            return;
        String pivot = strs[l];
        int i = l, j = r;
        while(i<j){
            while(i<j&&(pivot+strs[j]).compareTo(strs[j]+pivot)<=0)
                j--;
            if (i<j) {
                strs[i] = strs[j];
                i++;
            }
            while(i<j&&(strs[i]+pivot).compareTo(pivot+strs[i])<=0)
                i++;
            if (i<j) {
                strs[j] = strs[i];
                j--;
            }
        }
        strs[i] = pivot;
        quickSort(strs, l,i-1);
        quickSort(strs, i+1, r);
    }
}
```



