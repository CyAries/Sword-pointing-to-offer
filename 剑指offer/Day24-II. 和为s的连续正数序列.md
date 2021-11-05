## [Day24-II. 和为s的连续正数序列](https://leetcode-cn.com/problems/he-wei-sde-lian-xu-zheng-shu-xu-lie-lcof/)

题目

```tex
输入一个正整数 target ，输出所有和为 target 的连续正整数序列（至少含有两个数）。

序列内的数字由小到大排列，不同序列按照首个数字从小到大排列。
```

代码

```java
class Solution {
    public int[][] findContinuousSequence(int target) {
        int l = 1, r = 1;
        List<int[]> list = new ArrayList<>();
        while(r<target){
            int sum = getSum(l, r);
            if (sum>target){
                l++;
            }else if(sum==target){
                int[] ints = new int[r - l + 1];
                for (int i = 0; i < ints.length; i++) {
                    ints[i] = i+l;
                }
                list.add(ints);
                l++;
            }else{
                r++;
            }
        }
        return list.toArray(new int[list.size()][]);
    }
    public int getSum(int l, int r){
        return (l+r)*(r-l+1)/2;
    }
}
```

