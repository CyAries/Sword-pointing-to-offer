## [Day17-数据流中的中位数](https://leetcode-cn.com/problems/shu-ju-liu-zhong-de-zhong-wei-shu-lcof/)

题目

```tex
如何得到一个数据流中的中位数？如果从数据流中读出奇数个数值，那么中位数就是所有数值排序之后位于中间的数值。如果从数据流中读出偶数个数值，那么中位数就是所有数值排序之后中间两个数的平均值。

例如，

[2,3,4] 的中位数是 3

[2,3] 的中位数是 (2 + 3) / 2 = 2.5

设计一个支持以下两种操作的数据结构：

void addNum(int num) - 从数据流中添加一个整数到数据结构中。
double findMedian() - 返回目前所有元素的中位数。
```

代码

```java
class MedianFinder {
    Queue<Integer> A, B;
    public MedianFinder() {
        A = new PriorityQueue<>(); // 小顶堆 存储大的部分
        B = new PriorityQueue<>((x,y)->(y-x)); // 大顶堆 存储小的部分
    }
    public void addNum(int num) {
        if (A.size() == B.size()){
            B.add(num);
            A.add(B.poll());
        }else{
            A.add(num);
            B.add(A.poll());
        }
    }
    public double findMedian() {
        return A.size()==B.size()?(A.peek()+B.peek())/2.0:A.peek();
    }
}
```



