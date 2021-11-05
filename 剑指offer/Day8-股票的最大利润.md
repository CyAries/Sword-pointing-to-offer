## [Day8-股票的最大利润](https://leetcode-cn.com/problems/gu-piao-de-zui-da-li-run-lcof/)

题目

```tex
假设把某股票的价格按照时间先后顺序存储在数组中，请问买卖该股票一次可能获得的最大利润是多少？
```

代码

```java
class Solution {
    public int maxProfit(int[] prices) {
        if (prices.length == 0)
            return 0;
        int min = prices[0],max = 0;
        int k = 1;
        while(k<prices.length){
            if (prices[k]<min){
                min = prices[k];
            }else{
                int sub = prices[k] - min;
                if (sub>max)
                    max = sub;
            }
            k++;
        }
        return max;
    }
}
```

