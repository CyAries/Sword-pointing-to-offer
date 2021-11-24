## [Day30-数组中的逆序对](https://leetcode-cn.com/problems/shu-zu-zhong-de-ni-xu-dui-lcof/)

题目

```tex
在数组中的两个数字，如果前面一个数字大于后面的数字，则这两个数字组成一个逆序对。输入一个数组，求出这个数组中的逆序对的总数。
```

代码

归并排序

```java
class Solution {
    int len = 0;
    public int reversePairs(int[] nums) {
        int[] b = new int[nums.length];
        sort(nums,0,b.length-1,b);
        return len;
    }
    public void sort(int[] a,int begin,int end,int[] b){
        if (begin<end){
            int mid = begin+(end-begin)/2;
            sort(a, begin, mid, b);
            sort(a, mid+1, end, b);
            merge(a,begin,mid,end,b);
        }
    }
    public void merge(int[] a,int begin, int mid,int end,int[] b){
        int i = begin,j = mid+1,k = begin;
        while(i<=mid&&j<=end){
            if (a[i]<=a[j]){
                b[k++] = a[i++];
                len+=(j-mid-1);
            }else{
                b[k++] = a[j++];
            }
        }
        while(i<=mid){
            b[k++] = a[i++];
            len+=(end-mid);
        }
        while(j<=end){
            b[k++] = a[j++];
        }
        for (i = begin;i<=end;i++){
            a[i] = b[i];
        }
    }
}
```



