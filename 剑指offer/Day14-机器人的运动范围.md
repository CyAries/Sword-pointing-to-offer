## [Day14-机器人的运动范围](https://leetcode-cn.com/problems/ji-qi-ren-de-yun-dong-fan-wei-lcof/)

题目

```tex
地上有一个m行n列的方格，从坐标 [0,0] 到坐标 [m-1,n-1] 。一个机器人从坐标 [0, 0] 的格子开始移动，它每次可以向左、右、上、下移动一格（不能移动到方格外），也不能进入行坐标和列坐标的数位之和大于k的格子。例如，当k为18时，机器人能够进入方格 [35, 37] ，因为3+5+3+7=18。但它不能进入方格 [35, 38]，因为3+5+3+8=19。请问该机器人能够到达多少个格子？
```

代码

```java
class Solution {
    public int movingCount(int m, int n, int k) {
        // 向右和向下数组
        int[] a = {0, 1};
        int[] b = {1, 0};
        Queue<int[]> queue = new LinkedList<>();
        int size = 1;
        boolean[][] ret = new boolean[m][n];
        ret[0][0] = true;
        queue.offer(new int[]{0,0});
        while(!queue.isEmpty()){
            int[] poll = queue.poll();
            for (int i = 0; i < 2; i++) {
                int tx = poll[0] + a[i];
                int ty = poll[1] + b[i];
                if (tx<0||tx>=m||ty<0||ty>=n||ret[tx][ty]||get(tx)+get(ty)>k){
                    continue;
                }
                size++;
                ret[tx][ty] = true;
                queue.offer(new int[]{tx,ty});
            }
        }
        return size;
    }

    private int get(int x) {
        int res = 0;
        while (x != 0) {
            res += x % 10;
            x /= 10;
        }
        return res;
    }
}
```



