## [Day25-顺时针打印矩阵](https://leetcode-cn.com/problems/shun-shi-zhen-da-yin-ju-zhen-lcof/)

题目

```tex
输入一个矩阵，按照从外向里以顺时针的顺序依次打印出每一个数字。
```

代码

```java
class Solution {
    public int[] spiralOrder(int[][] matrix) {
        if (matrix.length == 0||matrix[0].length == 0)
            return new int[0];
        int[] a = new int[matrix.length*matrix[0].length];
        int k = 0;
        int begin = 0, end = matrix.length-1, left = 0,right = matrix[0].length-1;
        while(begin<=end||left<=right){
            if (begin<=end){
                for(int i = left;i<= right;i++){
                    a[k++] = matrix[begin][i];
                }
                begin++;
            }
            if (left<=right){
                for(int i = begin;i<=end;i++){
                    a[k++] = matrix[i][right];
                }
                right--;
            }
            if (begin<=end){

                for(int i = right;i>=left;i--){
                    a[k++] = matrix[end][i];
                }
                end--;
            }
            if (left<=right){
                for(int i = end;i>=begin;i--){
                    a[k++] = matrix[i][left];
                }
                left++;
            }
        }
        return a;
    }
}
```

