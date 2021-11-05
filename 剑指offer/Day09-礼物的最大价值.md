## [Day9-礼物的最大价值](https://leetcode-cn.com/problems/li-wu-de-zui-da-jie-zhi-lcof/)

题目

```tex
在一个 m*n 的棋盘的每一格都放有一个礼物，每个礼物都有一定的价值（价值大于 0）。你可以从棋盘的左上角开始拿格子里的礼物，并每次向右或者向下移动一格、直到到达棋盘的右下角。给定一个棋盘及其上面的礼物的价值，请计算你最多能拿到多少价值的礼物？
```

代码

```java
class Solution {
    public int maxValue(int[][] grid) {
        int max[][] = new int[grid.length][grid[0].length];
        max[0][0] = grid[0][0];
        for (int i = 1;i<grid.length;i++){
            max[i][0] = max[i-1][0]+grid[i][0];
        }
        for (int i = 1; i < grid[0].length; i++) {
            max[0][i] = max[0][i-1]+grid[0][i];
        }
        for (int i = 1;i<grid.length;i++){
            for (int j = 1;j<grid[0].length;j++){
                max[i][j] = Math.max(max[i-1][j],max[i][j-1])+grid[i][j];
            }
        }
        return max[max.length-1][max[0].length-1];
    }
}
```

