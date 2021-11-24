## [Day17-最小的k个数](https://leetcode-cn.com/problems/zui-xiao-de-kge-shu-lcof/)

题目

```tex
输入整数数组 arr ，找出其中最小的 k 个数。例如，输入4、5、1、6、2、7、3、8这8个数字，则最小的4个数字是1、2、3、4。
```

代码

```java
class Solution {
    public int[] getLeastNumbers(int[] arr, int k) {
        if (k<0)
            return null;
        int[] ints = new int[k];
        Arrays.sort(arr);
        System.arraycopy(arr, 0, ints, 0, ints.length);
        return ints;
    }
}
```

也可以使用大顶堆（这个比较好，应付面试官）

